# ShelfDock — 기기 연결 / Device sharing

0.1.2부터 초대 링크와 QR을 지원합니다. 최신 절차 / Invitation links and QR: [INVITATIONS.md](INVITATIONS.md)

## 한국어

공유는 기본적으로 꺼져 있습니다. 선반의 ⇄ 버튼에서 공유를 켜고 연결 설정을 적용합니다. 공유 중에는 **현재와 이후의 로컬 선반 내용 모두**가 페어링한 기기에 전달됩니다. 항목별 공개 범위 설정은 아직 없습니다. 파일 경로 자체는 전송하지 않습니다.

1. 두 Windows PC에서 공유를 켭니다. 인터넷 사용 시 공개 DHT 검색을 선택합니다.
2. 한 기기에서 일회용 코드를 만들고, 신뢰하는 경로로 다른 기기에 전달합니다. 코드는 10분 뒤 만료되며 한 번만 사용할 수 있습니다. 코드를 가진 기기에 연결 권한이 생깁니다.
3. 다른 기기의 코드 입력란에 붙여넣고 페어링합니다. 이후에는 같은 사용자 프로필과 기기 키를 유지하는 동안 재실행해도 연결이 유지됩니다.
4. 텍스트는 바로 표시됩니다. 8 MiB 이하의 캡처 이미지는 자동으로 받습니다. 일반 파일과 큰 캡처는 메타데이터만 표시합니다. 다운로드 버튼 또는 드래그 시도로 받은 후, 검증 완료 안내가 나오면 다시 드래그합니다.
5. 기기 상태에서 direct / relay / offline을 확인합니다. 연결 해제는 이후 접근을 막으며 이미 받은 사본은 회수하지 않습니다.

송신 기기가 온라인이고 원본이 남아 있어야 아직 받지 않은 파일을 다운로드할 수 있습니다. 송신 선반에서 제거해도 이미 전달된 항목 ID의 파일 참조는 남겨 둡니다. 원본 파일 변경·삭제나 캡처 캐시 정리 후에는 다운로드할 수 없습니다. 선반은 백업 서비스가 아닙니다. 원격 항목을 내 선반에서 제거해도 다른 기기에는 영향을 주지 않으며 재동기화로 다시 나타나지 않습니다.

파일은 SHA-256으로 전송 무결성을 확인한 뒤 로컬 캐시에 확정 저장합니다. SHA-256 검증은 악성 파일 검사나 게시자 인증이 아닙니다. 수신 파일은 자동 실행하지 않습니다. 수신 캐시는 항목 제거 후 최소 7일 보관하며 활성 목록·백업·실행 중 되돌리기가 참조하면 정리하지 않습니다.

### 외부망 릴레이 운영

Linux Docker/Unraid 실행 파일과 Compose 설정도 제공됩니다. 설치·허용 기기 등록·재시작·외부 포트 연결은 [RELAY-DOCKER.md](RELAY-DOCKER.md)를 참고하세요. Windows에서는 아래 명령을 그대로 사용할 수 있습니다.

기본 제공되는 공용 ShelfDock 릴레이는 없습니다. DHT는 주소 검색 기능이며 모든 NAT 환경을 통과시키지 않습니다. 직접 연결이 안 되면 공인 IP 또는 공인 주소로 포트가 연결된 **운영자 소유 서버**가 필요합니다. 서버 비용과 트래픽 비용은 운영자가 부담합니다.

Windows 서버에서 전체 배포 ZIP을 유지한 채 다음 명령을 실행합니다. `PEER_A`, `PEER_B`는 각 앱의 기기 화면에 표시되는 ID로 바꾸고, `203.0.113.10`은 실제 서버 공인 IP로 바꿉니다. 아래 주소는 문서용 예시입니다.

```powershell
.\ShelfDock.Peer.exe --relay --root C:\ShelfDockRelay\state --listen /ip4/0.0.0.0/tcp/4001 --announce /ip4/203.0.113.10/tcp/4001 --allow-peer PEER_A,PEER_B
```

운영자가 서버 방화벽·클라우드 보안 그룹에서 **선택한 TCP 4001 포트만** 허용해야 합니다. 보안 기능 전체를 끄지 마세요. 실행 후 `ready` JSON의 `peer`가 릴레이 ID입니다. 두 앱에 다음 주소를 입력하고 적용한 뒤, `릴레이 예약: True`를 확인하고 새 페어링 코드를 만듭니다.

```text
/ip4/203.0.113.10/tcp/4001/p2p/RELAY_PEER_ID
```

릴레이는 허용 목록에 등록된 송신·수신 기기만 중계합니다. 기기를 추가할 때 서버를 종료하고 목록을 수정해 같은 `--root`로 다시 실행합니다. 상태 폴더를 보관해야 릴레이 ID가 유지됩니다. Windows 기기 키는 해당 Windows 사용자 DPAPI로 보호되므로 폴더만 다른 서버로 옮겨서는 복원되지 않습니다. Ctrl+C로 종료합니다. 자동 서비스 등록이나 서버 배포는 이 버전에 포함하지 않습니다.

릴레이 기본 제한: 예약 16개, 기기당 회선 최대 4개, 한 회선 30분/8 GiB(프로토콜 오버헤드 포함). 따라서 8 GiB 파일 자체는 릴레이 한도에 걸릴 수 있습니다. 전송 재개는 지원하지 않습니다. 서버 중단·절전·방화벽 정책에 따라 연결이 실패할 수 있습니다. 포트 포워딩/홀 펀칭의 성공은 보장하지 않습니다.

### 데이터와 한계

- 앱 내부 통신은 별도 로컬 HTTP 포트 없이 자식 프로세스의 표준 입출력을 사용합니다.
- LAN 검색에는 mDNS, 인터넷 검색에는 공개 IPFS Kademlia DHT, 연결에는 libp2p를 사용합니다. DHT에는 선반 내용이나 파일명이 등록되지 않지만 IP·Peer ID 및 온라인 상태가 관찰될 수 있습니다.
- TCP·릴레이의 내용은 Noise, QUIC은 TLS로 보호됩니다. 릴레이 운영자는 주소·연결 시간·트래픽 양을 볼 수 있습니다. 완전한 익명성이나 침해 불가능성을 주장하지 않습니다.
- 공유 상대는 내 선반의 내용을 읽을 수 있습니다. 연결 코드는 공개 게시하지 마세요. 이미 받은 파일·텍스트는 연결 해제로 삭제되지 않습니다.
- 최대 16개 기기, 선반 500개 항목, 공유 파일 8 GiB, 공유 텍스트 한 항목 UTF-8 1 MiB, 전체 공유 목록 약 6 MiB. 공유 이력의 파일 참조는 최대 2,000개이며 초과하면 안내 후 공유 갱신을 거절합니다.
- 데이터는 `%LOCALAPPDATA%\ShelfDock`에 있습니다. `Network`는 신뢰 목록·내보낸 파일 참조·보호된 기기 키, `Received`는 받은 사본입니다. 원본 파일은 삭제하지 않습니다. 네트워크 상태가 손상되면 새 신뢰 목록으로 조용히 대체하지 않고 시작을 중단합니다.
- QR 코드, 모바일 앱, 전송 재개, 원격 삭제, 폴더 공유는 미지원입니다. 계정·클라우드 저장소·자동 사용 추적은 없습니다.

**검증 상태:** 로컬 기기 세 개로 DHT 검색·릴레이 전송·접근 제어를 검증합니다. 실제 서로 다른 외부망의 NAT/공인 릴레이 시험은 아직 완료하지 않았습니다. 이 검증 전까지 외부망 호환성을 보장하지 않고 공개 바이너리 출시는 보류합니다.

## English

Sharing is off by default. Open ⇄ Devices, enable sharing, and Apply. All current and future local shelf items are shared with paired devices; per-item sharing controls are not available. Create a single-use, ten-minute code on one device and enter it on the other over a trusted channel. Pairing persists across restarts. Never publish pairing codes.

Text mirrors immediately; captures up to 8 MiB download automatically. Other files appear as metadata. Click Download or attempt a drag, wait for verification, then drag again. The source must be online and its original file must remain available. Removing a shelf item does not delete copies elsewhere. Local removal is remembered so synchronization does not resurrect the item. This is not a backup service.

There is no included public relay service. To run your own Windows relay, retain the complete distribution and use the command above with your real public IP and both device IDs. Permit only its chosen TCP port through the server firewall and cloud security group. Read the relay peer ID from its ready JSON; enter the resulting `/ip4/PUBLIC_IP/tcp/4001/p2p/RELAY_ID` on both clients, Apply, wait for relay reservation, then generate a fresh pairing code. Stop with Ctrl+C. Keep the state directory and run as the same Windows user to retain the DPAPI-protected identity. The operator pays hosting and bandwidth costs. No service installation is automated.

The allowlisted relay supports 16 reservations, up to four circuits per peer, and 30 minutes/8 GiB per circuit including overhead. Large transfers may exceed that limit; resume is not supported. Hole punching cannot guarantee connectivity through every firewall or NAT.

DHT/mDNS expose peer IDs and network addresses, never the shelf catalog. TCP and circuit traffic use Noise; QUIC uses TLS. Relays can observe traffic metadata. Paired devices can read shared contents. Revocation blocks future access but cannot recall received copies. Downloads are SHA-256 checked, not malware-scanned, and never auto-executed.

Limits: 16 devices, 500 shelf items, 8 GiB/file, 1 MiB UTF-8/shared text item, approximately 6 MiB published catalog, 2,000 retained export references. Downloads live under `%LOCALAPPDATA%\ShelfDock\Received`; retired owned files are eligible for deletion after seven days only when no active item, backup or session undo refers to them. Original files are never cleanup targets.

Local automated DHT/relay tests do not prove public-network compatibility. External NAT/relay, cross-application drag, clean-Windows and mixed-DPI acceptance gates remain pending; the binary release stays a draft. No mobile support, QR pairing, folder transfer, cloud storage, telemetry, or automatic update.
