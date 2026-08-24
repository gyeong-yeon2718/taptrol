# 오픈소스 고지 / Third-Party Notices

`TaptrolReceiver.exe`는 아래 오픈소스 구성요소를 포함해 배포됩니다.
각 구성요소의 저작권은 원저작자에게 있으며, 아래 라이선스 조건에 따라 사용됩니다.

`TaptrolReceiver.exe` is distributed with the open-source components listed below. Each remains
the copyright of its authors and is used under the license shown.

| 구성요소 / Component | 버전 / Version | 라이선스 / License | 출처 / Source |
|---|---|---|---|
| pynput | 1.8.2 | **LGPL-3.0-only** | https://github.com/moses-palmer/pynput |
| websockets | 16.0 | BSD-3-Clause | https://github.com/python-websockets/websockets |
| cryptography | 49.0.0 | Apache-2.0 OR BSD-3-Clause | https://github.com/pyca/cryptography |
| winsdk | 1.0.0b10 | MIT | https://github.com/pywinrt/python-winsdk |
| six | 1.17.0 | MIT | https://github.com/benjaminp/six |
| CPython 런타임 / runtime | 3.12 | PSF-2.0 | https://github.com/python/cpython |

실행 파일은 PyInstaller로 패키징됩니다. PyInstaller의 부트로더는 GPL 예외 조항에 따라
독점 애플리케이션에 포함될 수 있습니다 — https://github.com/pyinstaller/pyinstaller

The executable is packaged with PyInstaller, whose bootloader carries a GPL exception that
permits inclusion in proprietary applications.

---

## pynput (LGPL-3.0) 관련 고지

`TaptrolReceiver.exe`에는 **pynput**이 포함되어 있으며, pynput은
**GNU Lesser General Public License version 3 (LGPL-3.0)** 로 배포됩니다.

- pynput의 전체 소스 코드는 위 링크와 PyPI(https://pypi.org/project/pynput/)에서
  누구나 받을 수 있습니다.
- LGPL-3.0 전문: https://www.gnu.org/licenses/lgpl-3.0.html
- GPL-3.0 전문(LGPL이 참조): https://www.gnu.org/licenses/gpl-3.0.html

**pynput을 직접 수정한 버전으로 교체하실 수 있습니다.** LGPL-3.0 제4조가 보장하는
권리이며, 아래 방법으로 행사하실 수 있습니다:

```
pip install pynput websockets cryptography winsdk
# 수정한 pynput을 대신 설치한 뒤 리시버를 소스에서 실행하거나 재패키징
```

리시버를 수정된 pynput과 다시 결합(relink)하는 데 필요한 자료가 더 필요하시면
gpgy2718@gmail.com 으로 요청해 주세요. LGPL-3.0이 요구하는 범위에서 제공해 드립니다.

**pynput** is included in `TaptrolReceiver.exe` under the LGPL-3.0. Its complete source is
publicly available at the links above. You have the right, under LGPL-3.0 section 4, to replace
the bundled pynput with a modified version of your own; if you need additional material to
relink the receiver against your build, request it at gpgy2718@gmail.com and it will be
provided to the extent the LGPL-3.0 requires.

---

Taptrol 자체 코드는 오픈소스가 아니며, 위 고지는 포함된 제3자 구성요소에만 적용됩니다.
Taptrol's own code is not open source; these notices cover the bundled third-party components only.
