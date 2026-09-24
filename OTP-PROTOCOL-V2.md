# ShelfDock pairing v2 — 0.2.0-beta

This replaces invitation v1 for new pairing at the user's explicit request. Existing trust and file protocols remain unchanged. Windows uses shared Go code; Mac must use the same IPC/protocol. Legacy invite/pair IPC and the /shelfdock/pair/1.0.0 stream handler are absent from the production peer. Historical transport fixtures remain test-only.

## Code and rendezvous

Default WSS endpoint: wss://shelfdock.mintflavor.ddns.net:4000/v1. Normal certificate/hostname validation is mandatory. Public WS is rejected; explicit loopback WS overrides support local integration fixtures only. Advanced operators can set SHELFDOCK_RENDEZVOUS or the Go --rendezvous flag to another WSS server.

App namespace: shelfdock.pairing.v2. Eight characters from 0–9/A–Z, displayed XXXX-XXXX. First TWO encode the allocated positive numeric mailbox nameplate as base36, zero-padded, maximum ZZ (1295). The remaining SIX are cryptographic rejection-sampled random characters (~31.02 secret bits); the two routing characters are PUBLIC. Never claim all eight characters provide 41-bit secret entropy. The complete code is the SPAKE2 password, never a public nameplate or hash lookup key. Full/over-capacity allocation fails closed.

One active session per process; one authentication attempt per session. Starts are limited to one per five seconds. Generator and receiver each begin a maximum 60-second monotonic context at initiation; after identity authentication the earlier signed Unix expiry also bounds approval. Any failure/cancellation/expiry closes the session and requires a fresh code. Backend memory-only mailboxes are periodically pruned; no guarantee is made about OS swap or physical memory erasure. Public names permit denial of service by occupying a slot; IP/global connection limits mitigate rather than eliminate this.

## Authentication and consent

Use gospake2 symmetric Ed25519 SPAKE2 (pinned d91629950ad1, MIT), also used by wormhole-william. This is not a claim of RFC 9382 wire interoperability or independent security audit. Do not implement curve arithmetic in ShelfDock.

Exchange phases in strict order: pake, identity, approved, ready, saved. Side IDs are fresh 24-character random identifiers. After a single peer PAKE message, reject additional sides, phase reordering and malformed inputs. Frame/message sizes and loop counts are bounded. Failed key confirmation burns the session.

AES-256-GCM protects post-PAKE messages using SHA256(sharedKey || appID), random 96-bit nonces, and appID/phase/sender side as associated data. The encrypted identity binds Peer ID, public key, display name, filtered addresses, issuer role and expiry. It carries a libp2p private-key signature over appID + canonical sorted side/PAKE transcript + identity JSON with a null signature. Validate key-to-Peer-ID equality, signature, opposite roles, distinct identities, field lengths and expiry. Display a matching 32-bit transcript-derived verification number plus full Peer IDs; names are untrusted display labels. Code+PAKE, not the short display number alone, authenticates the exchange.

Neither peer stores trust before its own explicit approval AND the encrypted approval of the other peer. An authenticated ready exchange precedes local durable save; an authenticated saved exchange precedes success UI and automatic sync. On failure after a local save, best-effort rollback removes the new trust. Distributed final-ack loss or rollback IO failure can leave an asymmetric stored pair; do not claim atomic cross-device commits. UI directs the user to inspect/unpair/retry. Pre-existing pairs are rejected without mutation.

No shelf information is exchanged through the mailbox. The server sees routing/traffic metadata and encrypted handshake payloads. File transport stays libp2p. No relay auto-enrollment is granted by OTP.

## IPC

- otpCreate: starts asynchronous generator session; returns id, phase, expires. Poll otpStatus for generated code.
- otpJoin {code}: starts receiver; returns session id. Accept case-insensitive input and optional hyphen, normalize to eight A–Z/0–9.
- otpStatus: id, phase, expires; code only while generator waits; authenticated peer/name/fingerprint at approval. Terminal phases clear code.
- otpApprove {id,accept}: one decision accepted only for matching unexpired approval phase.
- otpCancel {id}: cancels the matching unfinished session; stale IDs cannot cancel a newer session. Completed pairs require revoke.
- Phases: idle, connecting, waiting, approval, waiting-approval, complete, failed, cancelled.

UI must clear code on terminal state and on dialog close, sanitize remote display names, prevent approval before authentication, and show time remaining. Unknown/old invite/pair commands fail. Settings changes or peer shutdown cancel in-progress sessions. Do not log codes, key material or full IPC commands.

## Evidence

Local Go tests cover both approvals, matching identity/transcript, durable trust, wrong code, ciphertext tampering, rejection, cancellation/stale IDs, expiry, one-sided approval, retry limit, invalid input, public WS rejection, absent legacy stream handler and trust-save failure. Real WSS mailbox pairing passed from this LAN; independent WAN remains unverified. Windows IPC/UI tests cover removal of invitation/QR controls, OTP input, disabled approval, actual pair and verified remote file delivery. No independent cryptographic audit is claimed.

Sources: [Wormhole William](https://github.com/psanford/wormhole-william), [gospake2](https://salsa.debian.org/vasudev/gospake2), [mailbox server](https://github.com/magic-wormhole/magic-wormhole-mailbox-server).
