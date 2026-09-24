# ShelfDock v0.2.0-beta — OTP pairing (draft)

Windows 11 x64, self-contained, unsigned. Update BOTH devices for new pairing.

Invitation links and QR are completely replaced by an eight-character OTP. Generate on one device, enter on the other, compare device details/verification number, and approve on both within 60 seconds. Existing paired devices and shelf data remain. Failed/cancelled/expired codes require a new session.

WSS rendezvous now uses a valid TLS certificate, automated renewal/reload, request/connection/session limits and ephemeral mailbox state. File transport remains direct/DHT/libp2p relay; relay authorization is separate. OTP does not auto-enroll devices on the file relay.

Verified: local authentication failure/approval/expiry/save handling, Windows OTP IPC and file workflow, real WSS authentication from LAN, certificate renewal dry-run and rate limiting. Independent WAN, complete native target matrix, clean OS/DPI/performance and independent security audit remain pending; keep release draft. See OTP-GUIDE.md for incomplete-final-ack recovery and CHANGELOG.md.
