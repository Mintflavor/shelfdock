# ShelfDock User Guide (v0.2.4-beta)

8자리 OTP 연결 / OTP pairing: [OTP-GUIDE.md](OTP-GUIDE.md) · [P2P-GUIDE.md](P2P-GUIDE.md)

## 한국어

Windows 11 x64 및 macOS 13+ (Apple Silicon arm64)용 무료 작업 선반입니다. ZIP 전체를 폴더에 풀고 실행하세요. .NET 별도 설치, 관리자 권한, 계정은 필요하지 않습니다. 약관을 확인하고 동의하면 시작합니다.

- **실행 및 보안 경고**:
  - Windows: `ShelfDock.exe` 실행 시 SmartScreen 경고가 나타나면 [추가 정보] -> [실행]을 클릭하세요.
  - macOS: `ShelfDock.app` 실행 시 Gatekeeper 경고 발생 시 Finder에서 마우스 우클릭(Control+클릭) 후 [열기]를 선택하세요.
- **선반 열기**: Windows `Ctrl+Alt+S`, macOS `Command+Option+S` 또는 트레이/메뉴바 아이콘 클릭.
- 파일이나 일반 텍스트를 선반으로 끌어오세요. 캡처 이미지는 선반에서 붙여넣기(`Ctrl+V` / `Command+V`)하세요.
- 항목을 선택하고 다른 앱으로 끌어가세요. 다중 선택(`Ctrl`/`Command` 또는 `Shift` 클릭)을 지원합니다.
- 복사(`Ctrl+C` / `Command+C`): 선택한 항목 복사. 캡처 이미지는 이미지와 PNG 파일 형식으로 클립보드에 제공됩니다.
- 삭제(`Delete` / `Backspace`): 선반에서 참조 제거. 원본 파일은 절대 삭제하지 않습니다.
- 되돌리기(`Ctrl+Z` / `Command+Z`): 이번 실행 중 제거한 항목 복원.
- 고정(Pin): 자주 쓰는 항목을 상단에 고정하고 드롭 후 자동 제거에서 제외.
- 숨기기(`Esc` 또는 닫기 버튼): 트레이/메뉴바 아이콘으로 숨기기. 종료는 트레이/메뉴바 메뉴에서 선택하세요.

일반 파일은 경로만 기억하며 외부 전달은 복사만 허용합니다. 원본이 이동되거나 삭제되면 다시 추가해 주세요. 원본 파일이나 받은 캐시가 없으면 목록에 연한 빨강으로 표시됩니다.

드롭 완료 후 자동 제거(Auto-remove) 기능은 기본적으로 꺼져 있습니다. 켜면 대상 앱이 드롭을 수락한 후 고정하지 않은 항목을 선반에서 제거합니다. 업로드 성공 여부는 대상 앱에서 확인하세요. 실패하거나 취소된 드래그는 항목을 유지합니다.

설정은 변경 즉시 자동 반영됩니다. 설정과 선반 데이터는 로컬 앱데이터 폴더에 안전하게 보관됩니다. 최대 500개 항목, 텍스트 한 항목 100만 자, 붙여넣는 이미지 4천만 화소까지 지원합니다.

기기 간 공유는 기본 꺼짐입니다. ⇄ 버튼에서 8자리 OTP 페어링, 공개 DHT 검색, 자체 릴레이를 설정할 수 있습니다. 독립 외부망(WAN) 간 파일 전송 검증이 완료되었습니다. 자세한 내용은 [P2P-GUIDE.md](P2P-GUIDE.md)를 참고하세요.

플로팅 아이콘 옵션을 켜면 화면 최상단에 작은 드롭 타깃 아이콘이 유지됩니다. 아이콘에 파일·텍스트를 드롭하면 선반에 추가되며, 클릭 시 메인 선반이 열립니다.

### 수신 파일 캐시 및 보관 정책

다른 기기에서 수신한 파일 항목을 선반에서 직접 제거(`Delete`)하면 앱 전용 수신 캐시 파일도 함께 삭제됩니다. 송신자의 원본 파일과 사용자가 다른 폴더로 복사·내보낸 파일은 그대로 유지됩니다. 되돌리기는 항목 메타데이터를 복원하며, 삭제된 파일 내용은 송신 기기가 온라인일 때 다시 다운로드할 수 있습니다. 드롭 후 자동 제거 시에는 대상 앱의 파일 읽기/업로드 완료를 보호하기 위해 기존 보관 정책(7일 유예)을 유지합니다.

### Polar 후원 및 라이선스 키 활성화

ShelfDock의 모든 기능은 100% 무료이며 기능 제한이 없습니다. 개발자를 응원하고자 하는 사용자는 Settings -> About 탭의 Polar 후원 링크를 통해 후원할 수 있습니다. 발급받은 후원 라이선스 키는 딥링크(`shelfdock://license?key=YOUR_KEY`) 또는 앱 내 라이선스 입력창을 통해 자동으로 등록·인증할 수 있습니다.

---

## English

A free temporary work shelf for Windows 11 x64 and macOS 13+ (Apple Silicon arm64). Extract the entire ZIP and run the application. No separate runtime install, administrator rights, or account required.

- **Launch & Security**:
  - Windows: On SmartScreen prompt, click "More info" -> "Run anyway".
  - macOS: On Gatekeeper prompt, right-click (Control-click) `ShelfDock.app` in Finder and select "Open".
- **Open Shelf**: Windows `Ctrl+Alt+S`, macOS `Command+Option+S`, or click the tray/menubar icon.
- Drop local files or plain text. Paste screenshots with `Ctrl+V` (Windows) / `Command+V` (macOS).
- Select and drag items into target apps. Multi-selection supported via `Ctrl`/`Command` or `Shift` click.
- Copy (`Ctrl+C` / `Command+C`): Captures offer both bitmap and PNG formats to clipboard.
- Remove (`Delete` / `Backspace`): Removes references from the shelf; never deletes original files.
- Undo (`Ctrl+Z` / `Command+Z`): Restores items removed during the current session.
- Pin: Keeps items at the top and protects them from automatic cleanup.
- Hide (`Esc` or Close button): Hides to the system tray / menu bar.

File items retain paths only. Outgoing transfers allow Copy only. Pinned items appear first; missing files appear with a soft red background. Settings apply automatically without manual save buttons. Limits: 500 items, 1 million characters per text item, 40 megapixels per image.

P2P sharing is off by default. Open ⇄ Devices to configure 8-digit OTP pairing, public DHT discovery, and self-hosted relays. Verified on independent real-world public networks (WAN). See [P2P-GUIDE.md](P2P-GUIDE.md).

Floating icon mode keeps a minimal topmost drop target on screen. Drag items onto it to add them, or click to expand the full shelf.

### Received Cache & Retention Policy

Explicitly removing a received file via Delete also removes the corresponding app-owned download cache from disk. Sender originals and exported copies remain untouched. Undo restores metadata; deleted contents can be re-downloaded while the remote peer is online. Accepted-drop auto-remove maintains delayed retention to protect target application reading and uploading.

### Polar Sponsorship & License Deep-link

ShelfDock is 100% freeware with zero paywalls. Supporters may sponsor development via Polar link in Settings -> About. Donor license keys can be activated via direct deep-link (`shelfdock://license?key=YOUR_KEY`) or within the app's About interface.
