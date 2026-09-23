# ShelfDock 0.1.2-beta

초대 링크·QR 사용법 / Invitation links and QR: [INVITATIONS.md](INVITATIONS.md)

## 한국어

Windows 11 x64용 무료 작업 선반입니다. ZIP 전체를 폴더에 풀고 `ShelfDock.exe`를 실행하세요. .NET 별도 설치, 관리자 권한, 계정은 필요하지 않습니다. 약관을 확인하고 동의하면 시작합니다.

- `Ctrl+Alt+S`: 선반 열기. 설정에서 변경할 수 있습니다.
- 파일이나 일반 텍스트를 선반으로 끌어오세요. 캡처 이미지는 선반에서 `Ctrl+V`로 붙여넣으세요.
- 항목을 선택하고 다른 앱으로 끌어가세요. Ctrl/Shift 클릭으로 다중 선택할 수 있습니다.
- `Ctrl+C`: 선택한 항목 복사. 캡처 이미지는 이미지와 PNG 파일 형식으로 클립보드에 제공됩니다.
- `Delete`: 선반에서 제거. 원본 파일은 삭제하지 않습니다.
- `Ctrl+Z`: 이번 실행 중 제거한 항목 되돌리기.
- 고정: 자동 정돈에서 제외. 수동 제거는 가능합니다.
- `Esc` 또는 닫기 버튼: 트레이로 숨기기. 트레이 아이콘 더블클릭으로 다시 여세요. 종료는 트레이 메뉴에서 선택하세요.

일반 파일은 경로만 기억합니다. 파일 전달은 복사만 허용합니다. 선반 제거는 원본 삭제와 다릅니다. 원본이 이동·삭제되면 다시 추가해 주세요.

자동 정돈은 기본 꺼짐입니다. 켜면 대상 앱이 드롭을 수락한 후 고정하지 않은 항목을 제거합니다. 업로드 성공 여부는 대상 앱에서 확인하세요. 실패하거나 취소된 드래그는 항목을 유지합니다.

설정과 선반은 `%LOCALAPPDATA%\ShelfDock`에 저장합니다. 앱이 만든 PNG는 항목이 제거된 뒤 7일 이상 지나고 현재 항목·백업·실행 중 되돌리기에서 참조하지 않을 때 정리합니다. 정리는 앱 시작 시 수행합니다. 활성 항목에는 보관 만료가 없습니다.

최대 500개 항목, 텍스트 한 항목 100만 자, 붙여넣는 이미지 4천만 화소까지 지원합니다. 이미지 파일 미리보기는 32MB 이하에서 생성하며 나머지는 파일로 전달할 수 있습니다.

이 버전은 미서명 베타입니다. Windows가 게시자를 확인하지 못할 수 있습니다. 보안 기능을 해제하지 마세요. SHA-256은 파일 일치 여부를 확인하며 게시자 신원을 증명하지 않습니다.

폴더, 가상 메일 첨부파일, 혼합 유형 일괄 드래그, 여러 텍스트의 동시 드래그, 브라우저 이미지 URL 다운로드, 관리자 권한 대상 앱, 독점 전체 화면 위 표시는 지원 대상이 아닙니다. 클라우드 전용 파일은 먼저 로컬에 내려받으세요. 대상 앱이 드래그를 거절하면 복사·붙여넣기를 사용하세요.

업데이트는 GitHub Releases에서 새 ZIP을 다운로드해 종료한 앱의 폴더를 교체합니다. 사용자 데이터 폴더는 유지합니다. 자동 업데이트와 사용 추적은 없습니다.

기기 간 공유는 기본 꺼짐입니다. ⇄ 버튼에서 페어링·인터넷 DHT·사용자 운영 릴레이를 설정합니다. 원격 파일을 먼저 다운로드하고 검증이 끝나면 드래그하세요. 전체 설명과 외부망 검증 상태는 [P2P-GUIDE.md](P2P-GUIDE.md)를 참고하세요.

설정에서 **ShelfDock 아이콘을 화면에 항상 표시**를 켜면 작은 아이콘이 최상단에 유지됩니다. 아이콘에 파일·텍스트를 드롭하면 선반에 추가되며 가볍게 흔들립니다. 클릭하면 메인 선반을 열고 닫기/Esc를 누르면 아이콘으로 돌아갑니다. 아이콘을 끌어 위치를 옮길 수 있고 위치는 저장됩니다. Windows에서 애니메이션을 꺼 두면 흔들림도 생략합니다. 옵션을 끄면 기존 트레이 방식으로 돌아갑니다.

## English

A free temporary work shelf for Windows 11 x64. Extract the entire ZIP and run `ShelfDock.exe`. No separate .NET install, administrator rights, or account required. Read and accept the license on first launch.

- `Ctrl+Alt+S`: open the shelf; customize in Settings.
- Drop local files or plain text. Use `Ctrl+V` to paste a screenshot.
- Select and drag items into another app. Ctrl/Shift-click selects multiple items.
- `Ctrl+C`: copy. Captures offer both bitmap and PNG-file clipboard formats.
- `Delete`: remove references from the shelf, never the original files.
- `Ctrl+Z`: undo removals during the current session.
- Pin keeps items out of automatic cleanup. Manual removal is still available.
- `Esc` / Close hides to the tray. Double-click the tray icon to return; use its menu to Quit.

File items retain paths only. Outgoing transfers allow Copy only. Moved/deleted originals must be added again. Auto-remove is off by default; if enabled, an accepted drop removes unpinned shelf items. Accepted does NOT mean an upload has completed. Cancelled/rejected drops retain items.

State is saved in `%LOCALAPPDATA%\ShelfDock`. Generated PNGs become eligible for cleanup seven days after removal, only when not referenced by the active shelf, recovery backup or session undo. Cleanup runs on startup. Active items do not expire. Limits: 500 items, 1 million characters per text item, 40 megapixels per pasted image. Thumbnails are generated for image files up to 32MB; other files can still be transferred.

Unsigned beta: Windows may not verify the publisher. Do not disable security features. SHA-256 verifies file identity, not publisher authenticity.

Unsupported: folders, virtual mail attachments, mixed-type batch drags, multiple text items in a drag, remote image-URL downloads, elevated target apps, exclusive fullscreen overlays. Download cloud-only files locally first. If an app rejects drag-and-drop, try Copy/Paste.

Updates are manual: quit, download the next ZIP from Releases, and replace the application folder. Keep the user-data folder. No automatic telemetry or updates.

Official releases and feedback: https://github.com/Mintflavor/shelfdock

Paired-device sharing is off by default. Open ⇄ to configure pairing, public DHT discovery and your own relay. Download remote files before dragging. See [P2P-GUIDE.md](P2P-GUIDE.md) for privacy, relay operation and pending external-network validation.

Enable **Keep a floating ShelfDock icon on screen** in Settings for a persistent topmost drop target. Drop files/text onto it, click to open the shelf, and Close/Esc to return to the icon. Drag the icon to reposition it; its position is saved. The subtle drag animation follows Windows animation preferences. Disabling the option restores tray-only behavior. Docker relay setup: [RELAY-DOCKER.md](RELAY-DOCKER.md).
License: LICENSE.txt (English governs); LICENSE.ko.md explains it in Korean.
