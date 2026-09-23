# ShelfDock Relay — Docker / Unraid

Linux amd64 relay package. The desktop application remains Windows-only.

## Unraid 설치

1. 릴레이 tar.gz를 `/mnt/user/appdata/shelfdock-relay`에 풉니다. `image/`에는 실행 파일과 라이선스만 있으며 ShelfDock 자체 소스는 없습니다.
2. 아래 명령으로 상태·설정 폴더를 준비합니다. 이 경로는 릴레이 전용이어야 합니다.

```sh
cd /mnt/user/appdata/shelfdock-relay
mkdir -p state config
chown 65532:65532 state
chmod 700 state
cp -n allowed-peers.example.txt config/allowed-peers.txt
cp -n .env.example .env
```

3. `.env`의 `SHELFDOCK_RELAY_ANNOUNCE`를 서버 주소로 수정합니다. 먼저 `/ip4/Unraid내부IP/tcp/4001`로 LAN 시험할 수 있습니다. `config/allowed-peers.txt`에는 앱 ⇄ 화면의 Peer ID를 한 줄에 하나씩 넣습니다. 빈 목록은 모든 기기를 거부합니다.
4. 실행합니다.

```sh
docker compose up -d --build
docker compose ps
docker compose logs --tail=10 shelfdock-relay
```

로그 `ready.data.peer`가 릴레이 ID입니다. 앱에 `/ip4/서버주소/tcp/4001/p2p/릴레이ID`를 입력합니다. 두 기기 모두 허용 목록에 있어야 합니다. 목록 변경은 새 예약·회선부터 적용되며, 기존 연결을 즉시 끊으려면 `docker compose restart`가 필요합니다.

컨테이너는 비 root UID 65532, 읽기 전용 루트 파일시스템, 전용 상태 볼륨, 권한 제거, 메모리 256 MiB/CPU 1개 제한으로 실행됩니다. 이 자원 제한은 초기 운영 설정이며 부하 보장값이 아닙니다. 로그는 5 MB × 3으로 제한합니다. healthcheck는 TCP 수신 상태만 확인하므로 실제 중계 시험을 대신하지 않습니다. SIGTERM 종료와 `unless-stopped` 재시작 정책을 지원합니다.

### 외부 접속

Unraid는 대개 공유기 안쪽에 있습니다. 컨테이너 설치만으로 공인 릴레이가 되지는 않습니다.

- 공유기 TCP 외부 포트 → Unraid IP의 해당 호스트 포트로 포워딩합니다.
- `.env`에 `/ip4/실제공인IP/tcp/외부포트` 또는 `/dns4/도메인/tcp/외부포트`를 지정하고 `docker compose up -d`로 반영합니다.
- 일반 HTTP 리버스 프록시 경로로 이 프로토콜을 전달할 수 없습니다. TCP 전달이 필요합니다.
- CGNAT 환경이면 일반 포트 포워딩으로 외부에서 도달하지 못할 수 있습니다. 별도 공인 IP 환경이 필요합니다.
- 외부망에서 `Test-NetConnection 공인주소 -Port 포트`로 TCP 도달을 확인한 뒤 실제 앱 전송을 시험합니다. TCP 성공만으로 릴레이 성공을 판단하지 않습니다.

`state/identity.protected`를 포함한 상태 디렉터리를 보관하면 재시작·이미지 교체 후에도 릴레이 ID가 유지됩니다. Linux에서는 키가 파일 접근 권한으로 보호되며 Windows DPAPI 암호화 파일과 호환되지 않습니다. 허용 목록에는 공개 기기 ID만 넣고 개인 키는 공유하지 마세요. 삭제 없이 `docker compose down`으로 중단할 수 있습니다. 이미지 갱신은 새 `image/`를 배치하고 `docker compose up -d --build`로 수행합니다.

기본 회선 제한은 30분/8 GiB(오버헤드 포함), 예약 16개입니다. 전송 재개와 무제한 공개 릴레이 운영은 지원하지 않습니다. 제3자 소스 및 고지는 `image/licenses`에 포함되어 있습니다.

## English

Extract into a dedicated Unraid appdata folder. Create `state` owned by UID 65532, copy the configuration examples, set the advertised address and put one allowed device Peer ID per line in `config/allowed-peers.txt`. Empty or invalid lists deny new access. Run `docker compose up -d --build`. The ready log contains the stable relay Peer ID. Both endpoints must be allowlisted. Restart to terminate existing circuits after revocation.

The container is non-root, read-only except for `/data`, resource-limited and restartable. Its TCP healthcheck does not prove successful relay traffic. Keep the state volume across upgrades. Linux identities rely on file permissions, not Windows DPAPI. WAN service additionally requires a publicly reachable TCP port and an advertised public IP/domain; Docker installation alone does not configure your router or overcome CGNAT. See P2P-GUIDE.md for privacy and protocol limits.
