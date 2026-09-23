# PC 초대 링크 및 QR — 0.1.2-beta

1. 양쪽 PC에서 새 ZIP 전체를 풀고 ShelfDock.exe를 한 번 실행합니다. 현재 사용자에게 shelfdock: 링크 열기가 등록됩니다. 설치 폴더를 옮겼다면 새 위치에서 앱을 다시 실행하세요.
2. 초대하는 PC의 ⇄ 기기 화면에서 공유 설정을 적용하고 **초대 링크 + QR 만들기**를 누릅니다.
3. **초대 링크 복사**로 상대 PC에 전달합니다. QR은 화면에 표시하거나 **QR을 PNG로 저장**할 수 있습니다. 링크와 QR은 동일한 초대입니다.
4. 받는 PC에서 링크를 열면 ShelfDock 연결 화면이 나타납니다. **확인 후 연결**을 누르고 상대 기기 ID와 공유 안내를 확인해 승인합니다. 링크를 열기만 해서는 연결·공유를 시작하지 않습니다.
5. 메신저가 사용자 지정 링크를 클릭 가능하게 표시하지 않으면 ⇄ 화면에 링크를 붙여넣으세요. 앱을 실행 중이어도 초대를 받을 수 있습니다.

초대는 10분 유효·1회 사용입니다. 새 초대를 만들면 이전 초대는 무효입니다. 내 기기에만 전달하세요. 연결 후 현재와 이후의 선반 내용이 공유됩니다. QR이 너무 커서 생성되지 않으면 링크를 사용하세요. PC QR 스캔·이미지 읽기와 모바일 공유는 이번 버전에 포함하지 않았습니다.

외부망 연결에는 기존 릴레이 설정과 양쪽 기기의 서버 허용 목록 등록이 여전히 필요합니다. 초대 링크는 릴레이 사용 권한을 부여하지 않습니다. 기존 Unraid 컨테이너는 교체할 필요가 없습니다.

## English

Run the new ShelfDock.exe once on each PC to register the per-user shelfdock: URL handler. Create an invitation link + QR in Devices, copy the link or save the QR as PNG, and open the link on the receiving PC. Review the peer and explicitly confirm sharing before connecting. Running instances receive the invitation through a current-user, session-scoped local pipe. If a messenger does not recognize custom URL schemes, paste the link in Devices. Moving the app requires running it from the new location again.

Invitations expire after ten minutes and work once; creating a new invitation replaces the previous one. QR scanning/import is not included. Relay configuration and device allowlisting remain separate requirements.

## Focused validation

Focused invitation checks: strict link parsing, expiry and size rejection, exact payload preservation, independent QR decoding, bounded running-instance forwarding, actual two-peer pairing and replay denial (13 checks). The release WPF build and 30 baseline storage checks also passed during packaging; packaging checks the source/data guard and bundled notices. No repeat WAN, DPI, performance or broad unrelated regression sweep was requested.
