# 개인정보처리방침 / Privacy Policy

**앱**: Taptrol (`io.github.gyeongyeon2718.taptrol`)
**최종 수정**: 2026-08-07
**문의**: gpgy2718@gmail.com

---

## 한국어

### 요약

Taptrol은 **개인정보를 수집하지 않습니다.** 개발자가 운영하는 서버가 없고, 광고·분석 SDK도
포함하지 않습니다. 앱이 만드는 모든 데이터는 사용자의 워치와 PC에만 저장되며, 통신은 사용자의
로컬 Wi-Fi 안에서 워치와 PC 사이에서만 일어납니다.

### 기기에 저장되는 데이터

페어링한 PC에 다시 연결하려면 아래 값이 필요합니다. **전부 로컬에만 저장되며 외부로 전송되지
않습니다.**

**워치에 저장 (Android KeyStore로 AES-256-GCM 봉인, 앱 전용 저장소):**

| 항목 | 용도 |
|---|---|
| PC IP 주소 | 다음 실행 시 재연결 |
| PC 서버 ID | 페어링한 PC 식별 |
| PC 인증서 지문 (SHA-256) | 접속 대상이 그 PC가 맞는지 검증 |
| pair secret (32바이트) | 세션 인증(HMAC) |
| 워치 client ID | PC가 이 워치를 식별 |
| 감도·언어 설정 | 사용자 설정 유지 |

**PC에 저장 (`%APPDATA%\Taptrol\`, Windows DPAPI로 봉인):**

| 항목 | 용도 |
|---|---|
| PC 자체 서명 인증서와 개인키 | TLS 연결 |
| 등록된 워치 목록 (기기 이름, client ID, pair secret) | 재연결 시 인증 |
| 로컬 로그 (`taptrol.log`) | 문제 진단 |

로그에는 연결 상태, 오류 메시지, 접속 IP가 기록됩니다. 로그는 PC에만 남고 자동으로 전송되지
않습니다.

### 전송되는 데이터

워치와 PC 사이에만 오갑니다. 인터넷을 거치지 않습니다.

- 커서 이동량, 클릭, 스크롤, 슬라이드 이동 키 입력
- 페어링·인증 메시지

모든 통신은 **인증서 고정(certificate pinning)을 적용한 TLS 1.2 이상**으로 암호화됩니다.

### 수집하지 않는 것

- 계정, 이름, 이메일, 전화번호
- 위치 정보
- 연락처, 사진, 파일
- 화면 내용, 입력한 문자
- 사용 통계, 크래시 리포트, 광고 식별자

### 데이터 삭제

- **워치**: 앱을 삭제하면 저장된 데이터가 모두 지워집니다. 앱 안에서 `연결 해제` 후
  등록을 해제할 수도 있습니다.
- **PC**: 리시버 창의 `등록된 워치 목록`에서 개별 해제할 수 있습니다. 전체 삭제는
  `%APPDATA%\Taptrol\` 폴더를 지우면 됩니다.

### 아동 개인정보

만 13세 미만 아동을 대상으로 하지 않으며, 아동으로부터 어떠한 정보도 수집하지 않습니다.

### 제3자 제공

없습니다. 데이터를 전송할 서버가 존재하지 않습니다.

### 변경 고지

이 방침이 변경되면 이 문서와 GitHub Release 노트에 반영합니다.

---

## English

### Summary

Taptrol **collects no personal data.** There is no developer-operated server, and no
advertising or analytics SDK is bundled. Everything the app produces stays on the user's
watch and PC, and all traffic happens between those two devices on the user's own Wi-Fi.

### Data stored on your devices

The values below are what makes reconnecting to a paired PC possible. **All of it is local
and none of it is transmitted anywhere.**

**On the watch** (sealed with AES-256-GCM via the Android KeyStore, in app-private storage):
the PC's IP address, its server ID, its certificate SHA-256 fingerprint, the 32-byte pair
secret, this watch's client ID, and your sensitivity and language preferences.

**On the PC** (`%APPDATA%\Taptrol\`, sealed with Windows DPAPI): the PC's self-signed
certificate and private key, the list of registered watches (device name, client ID, pair
secret), and a local log file recording connection state, errors and peer IP addresses. The
log stays on the PC and is never uploaded.

### Data in transit

Only between the watch and the PC, never over the internet: cursor deltas, clicks, scrolls,
slide-control keystrokes, and the pairing/authentication messages. All of it runs over
**TLS 1.2+ with certificate pinning**.

### Not collected

Accounts, names, emails, phone numbers, location, contacts, photos, files, screen contents,
typed text, usage analytics, crash reports, advertising identifiers.

### Deleting your data

Uninstalling the watch app removes everything it stored. On the PC, individual watches can be
revoked from the receiver's registered-device list, and deleting `%APPDATA%\Taptrol\` removes
all of it.

### Children

Not directed at children under 13; no information is knowingly collected from them.

### Third parties

None. There is no server to send anything to.

### Changes

Any change to this policy will be reflected in this document and in the GitHub release notes.
