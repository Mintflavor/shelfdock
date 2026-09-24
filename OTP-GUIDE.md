# ShelfDock 0.2.0 — 8자리 OTP 연결

양쪽 PC에 0.2.0 이상을 실행하세요. 기존에 연결한 기기는 그대로 유지됩니다. 새 연결에는 초대 링크와 QR을 사용하지 않습니다.

1. 양쪽 ⇄ 기기 화면에서 공유를 켭니다.
2. 한쪽에서 **8자리 코드 만들기**를 누릅니다.
3. 다른 쪽에서 코드를 입력하고 **코드로 연결**을 누릅니다. 하이픈과 소문자 입력도 처리합니다.
4. 양쪽에 표시된 기기 이름·Peer ID·확인 번호를 비교합니다. 같은 확인 번호와 내 기기임을 확인한 뒤 체크하고 **이 기기 승인**을 양쪽에서 누릅니다.
5. 양쪽에 연결 완료가 표시되면 선반 공유를 시작합니다.

코드 생성부터 양쪽 승인까지 총 60초입니다. 잘못된 코드, 거절, 취소, 시간 초과, 창 닫기, 앱 종료·연결 설정 변경은 새 코드로 다시 시작하세요. 재시도는 최소 5초 간격입니다. 상대가 이미 연결되어 있으면 새로 인증할 필요가 없습니다.

인증에는 인터넷의 WSS 랑데부 서버가 필요합니다. 서버가 일시 중단돼도 기존 연결의 파일 전송은 기존 직접/DHT/릴레이 경로를 사용합니다. OTP 연결은 파일 릴레이 허용 목록 등록을 대신하지 않습니다.

이전 shelfdock: 링크·QR·초대 토큰은 더 이상 수락하지 않습니다. 새 버전은 자신이 등록했던 Windows URL 연결을 정리합니다. 이전 버전과 새 버전 사이의 신규 페어링은 지원하지 않으므로 양쪽을 업데이트하세요. 기존 신뢰 목록과 선반 데이터는 유지합니다.

드물게 최종 저장 확인 중 연결이 끊기면 한쪽에만 기기가 남을 수 있습니다. 양쪽 기기 목록을 확인하고 남은 항목을 연결 해제한 뒤 새 코드로 다시 시도하세요. 완료가 불확실한 상태를 성공으로 표시하지 않습니다.

## English

Run 0.2.0+ on both PCs. Enable sharing in Devices, generate a code on one, and enter it on the other. Compare device names, Peer IDs and the verification number on both screens; check the confirmation box and approve on BOTH devices within the original 60-second deadline. Retry with a new code after rejection, cancellation, failure or expiry. Retry interval is at least five seconds.

Invitation URLs/QR and old tokens are no longer accepted. Existing paired devices and shelf data remain intact. WSS rendezvous is needed for new pairing; bulk files still use direct/DHT/libp2p relay transport and relay allowlisting is separate. If final acknowledgement is interrupted, review both device lists, unpair any incomplete entry, and retry. No automatic reconnection of an unapproved session.
