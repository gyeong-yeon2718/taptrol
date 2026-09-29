# 개인정보처리방침 / Privacy Policy

**앱**: Taptrol — 워치 앱 (`io.github.gyeongyeon2718.taptrol`), 폰 앱 (`io.github.gyeongyeon2718.taptrol.phone`), PC 리시버
**최종 수정**: 2026-09-29
**문의**: gpgy2718@gmail.com

---

## 한국어

### 요약

Taptrol은 **개인정보를 수집하지 않습니다.** 개발자가 운영하는 서버가 없고, 광고·분석 SDK도
포함하지 않습니다. 앱이 만드는 모든 데이터는 사용자의 워치·폰과 PC에만 저장되며, 통신은 사용자의
로컬 Wi-Fi 안에서 워치·폰과 PC 사이에서만 일어납니다. 워치 앱과 폰 앱은 같은 방식으로 동작하며,
아래 설명은 두 앱 모두에 해당합니다.

```
Taptrol 계정 없음
Taptrol 클라우드 없음
광고 없음
분석 없음
PC ↔ 워치·폰 로컬 제어
결제는 Google Play가 처리
```

외부 연결은 두 가지뿐입니다.

- **Taptrol Pro 구매** — Google Play가 처리하며, 개발자는 결제 정보에 접근하지 않습니다.
  무료로만 쓰시면 이 경로는 동작하지 않습니다.
- **PC 리시버의 업데이트 확인** (9.10.0부터) — 켜져 있으면 하루 한 번 GitHub
  (`api.github.com`)에 공개 다운로드 저장소의 최신 버전 번호를 묻습니다. 요청에는 리시버 버전
  외에 아무것도 담기지 않으며(워치·폰·페어링·사용 기록 없음), 일반적인 웹 요청처럼 GitHub이 PC의
  IP 주소를 볼 수 있습니다. 개발자는 이 요청을 받지도 보지도 않습니다. 리시버의
  `설정 → 새 버전 자동 확인`에서 끌 수 있고, Microsoft Store 버전은 확인하지 않습니다.

### 기기에 저장되는 데이터

페어링한 PC에 다시 연결하려면 아래 값이 필요합니다. **전부 로컬에만 저장되며 외부로 전송되지
않습니다.**

**워치·폰에 저장 (Android KeyStore로 AES-256-GCM 봉인, 앱 전용 저장소):**

| 항목 | 용도 |
|---|---|
| PC IP 주소 | 다음 실행 시 재연결 |
| PC 서버 ID | 페어링한 PC 식별 |
| PC 인증서 지문 (SHA-256) | 접속 대상이 그 PC가 맞는지 검증 |
| pair secret (32바이트) | 세션 인증(HMAC) |
| 기기 client ID | PC가 이 워치·폰을 식별 |
| 감도·언어·스크롤·진동 설정 | 사용자 설정 유지 |
| Pro 구매 여부 (참/거짓) | 오프라인에서도 구매한 기능을 계속 쓰기 위함. 결제 토큰이나 계정 식별자는 저장하지 않습니다 |

**PC에 저장 (`%APPDATA%\Taptrol\`, Windows DPAPI로 봉인):**

| 항목 | 용도 |
|---|---|
| PC 자체 서명 인증서와 개인키 | TLS 연결 |
| 등록된 기기 목록 (기기 이름, client ID, pair secret) | 재연결 시 인증 |
| 리시버 설정 (자동 실행, 업데이트 확인, 폰 키보드 입력 허용) | 사용자 설정 유지 |
| 로컬 로그 (`taptrol.log`) | 문제 진단 |

로그에는 연결 상태, 오류 메시지, 접속 IP가 기록됩니다. **폰에서 입력한 문자는 로그에 기록하지
않습니다** (진단용 디버그 모드에서도 입력 내용은 가립니다). 로그는 PC에만 남고 자동으로 전송되지
않습니다.

### 전송되는 데이터

워치·폰과 PC 사이에만 오갑니다. 인터넷을 거치지 않습니다.

- 커서 이동량, 클릭, 스크롤, 슬라이드 이동 키 입력
- **폰 앱의 키보드 탭에서 입력한 문자와 특수 키·단축키** — 사용자의 PC에 입력하기 위해 보내며,
  폰에도 PC에도 저장·기록하지 않습니다. PC 리시버의 `설정 → 폰에서 키보드 입력 허용`을 끄면
  PC가 받지 않습니다
- 페어링·인증 메시지
- **직전 실행에서 앱이 종료된 경우, 그 요약 한 줄** (오류 종류, 발생 시각, 앱 버전, 호출 위치).
  세션당 한 번만 보내고 워치·폰에서는 지웁니다. PC의 로컬 로그(`taptrol.log`)에만 기록되며,
  개발자를 포함해 누구에게도 전송되지 않습니다. 사용자가 입력한 내용은 담기지 않습니다

모든 통신은 **인증서 고정(certificate pinning)을 적용한 TLS 1.2 이상**으로 암호화됩니다.

### 수집하지 않는 것

- 계정, 이름, 이메일, 전화번호
- 위치 정보
- 연락처, 사진, 파일
- 화면 내용
- 입력한 문자 — 폰 키보드로 친 글자는 사용자 본인의 PC에 입력되기 위해 전송될 뿐, 개발자나
  제3자에게 가지 않고 어디에도 저장되지 않습니다
- 사용 통계, 광고 식별자
- 크래시 리포트 — **외부로 전송하지 않습니다.** 서드파티 크래시 SDK를 넣지 않았고,
  요약은 사용자 본인의 워치·폰과 본인의 PC 사이에서만 오갑니다
- 결제 수단 정보 (Google Play가 처리하며 앱은 접근하지 않습니다)

### 데이터 삭제

- **워치·폰**: 앱을 삭제하면 저장된 데이터가 모두 지워집니다. 폰 앱은 `설정 → 등록된 PC`에서
  PC별로 삭제할 수도 있습니다.
- **PC**: 리시버 창의 `등록된 기기` 목록에서 기기별로 등록 해제할 수 있습니다. 전체 삭제는
  `%APPDATA%\Taptrol\` 폴더를 지우면 됩니다.

### 아동 개인정보

만 13세 미만 아동을 대상으로 하지 않으며, 아동으로부터 어떠한 정보도 수집하지 않습니다.

### 제3자 제공

Taptrol 개발자는 데이터를 전송할 서버를 운영하지 않습니다.

다만 **Taptrol Pro 구매는 Google Play가 처리합니다.** 결제 과정에서 Google이 수집·처리하는
정보는 Google의 개인정보처리방침을 따르며, Taptrol 개발자는 다음에 접근하지 않습니다.

* 결제 수단 정보 (카드번호 등)
* 이름, 주소, 이메일
* Google 계정 정보

앱은 Google Play에 **"이 사용자가 Pro를 구매했는가"** 만 질의하고, 그 결과(참/거짓)를 워치·폰에
저장합니다. 구매 여부 자체도 개발자 서버로 전송되지 않습니다.

무료로만 사용하시면 Google Play Billing은 동작하지 않습니다.

### 변경 고지

이 방침이 변경되면 이 문서와 GitHub Release 노트에 반영합니다.

---

## English

### Summary

Taptrol **collects no personal data.** There is no developer-operated server, and no
advertising or analytics SDK is bundled. Everything the apps produce stays on the user's
watch or phone and PC, and all traffic happens between those devices on the user's own Wi-Fi.
The watch app and the phone app work the same way; everything below applies to both.

```
No Taptrol account
No Taptrol cloud
No advertising
No analytics
Local PC <-> watch/phone control
Purchase handled by Google Play
```

There are only two external interactions:

- **A Taptrol Pro purchase**, which Google Play handles and the developer never sees the details
  of. Stay on the free tier and that path is never used.
- **The PC receiver's update check** (from 9.10.0). When enabled, once a day it asks GitHub
  (`api.github.com`) for the latest version number of the public download repository. The request
  carries nothing but the receiver's version — no watch, phone, pairing or usage information — and, like
  any web request, GitHub can see the PC's IP address. The developer neither receives nor sees
  it. Turn it off in the receiver under `Settings → Check for new versions automatically`; the
  Microsoft Store build does not check at all.

### Data stored on your devices

The values below are what makes reconnecting to a paired PC possible. **All of it is local
and none of it is transmitted anywhere.**

**On the watch or phone** (sealed with AES-256-GCM via the Android KeyStore, in app-private
storage): the PC's IP address, its server ID, its certificate SHA-256 fingerprint, the 32-byte
pair secret, this device's client ID, and your sensitivity, language, scrolling and vibration
preferences.

**On the watch or phone, additionally**: whether Pro has been purchased, stored as a single boolean so
the app keeps working offline. No purchase token or account identifier is kept.

**On the PC** (`%APPDATA%\Taptrol\`, sealed with Windows DPAPI): the PC's self-signed
certificate and private key, the list of registered devices (device name, client ID, pair
secret), the receiver's settings, and a local log file recording connection state, errors and
peer IP addresses. **Text typed on a phone is never written to the log**, not even in the
diagnostic debug mode. The log stays on the PC and is never uploaded.

### Data in transit

Only between the watch or phone and the PC, never over the internet: cursor deltas, clicks,
scrolls, slide-control keystrokes, and the pairing/authentication messages. All of it runs over
**TLS 1.2+ with certificate pinning**.

**Text and keys typed in the phone app's Keyboard tab** are sent to your PC so that they are
typed there. They are not stored on the phone or the PC. Turn off
`Settings → Allow typing from a phone` in the PC receiver and the PC ignores them.

If the app closed unexpectedly on its previous run, one line summarising it (error type, time,
app version, call site) is sent once per session and then erased from the watch or phone. It is
written only to the PC's local log and goes to nobody, the developer included. It contains
nothing you typed.

### Not collected

Accounts, names, emails, phone numbers, location, contacts, photos, files, screen contents,
usage analytics, advertising identifiers. Text you type on the phone goes only to your own PC,
to be typed there; it is not collected by the developer or anyone else and is stored nowhere.

Crash reports are **never sent anywhere**. There is no third-party crash SDK in this app; the
summary described above travels only between your own watch or phone and your own PC.

### Deleting your data

Uninstalling the watch or phone app removes everything it stored; the phone app can also forget
a PC under `Settings → Paired PCs`. On the PC, individual devices can be revoked from the
receiver's registered-device list, and deleting `%APPDATA%\Taptrol\` removes
all of it.

### Children

Not directed at children under 13; no information is knowingly collected from them.

### Third parties

The Taptrol developer operates no server to send anything to.

**Taptrol Pro purchases are handled by Google Play.** Whatever Google collects during a
purchase is governed by Google's own privacy policy; the Taptrol developer never sees payment
details, names, addresses, emails, or Google account information.

The app asks Google Play one question — whether this user owns Pro — and stores the yes/no
answer on the watch or phone. Even that answer is never sent to a developer server.

If you only use the free tier, Google Play Billing is never contacted.

### Changes

Any change to this policy will be reflected in this document and in the GitHub release notes.
