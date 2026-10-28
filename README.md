# MediChart EMR 연동 자료 — 고려대학교 구로병원

고려대학교 구로병원 EMR(Delphi)과 MediChart 를 연동하실 때 쓰시는 라이브러리 · 예제 · 실행 파일과 개발 가이드를 배포하는 저장소입니다.
이 저장소에는 소스 코드를 두지 않으며, 연동 자료는 **릴리스(Releases)** 로만 제공해 드립니다.

## 최신 자료 받기

**<https://github.com/gninraw/MediChart-KMC/releases/latest>**

위 주소는 늘 가장 최근 릴리스를 가리킵니다. 릴리스 아래 **Assets** 에서 `MediChart-KMC-v<버전>.zip` 을 받아 주십시오.
새 버전이 나오면 이전 버전은 [전체 릴리스 목록](https://github.com/gninraw/MediChart-KMC/releases)에 남으며, 제목에 '(구버전)' 이 붙습니다.
이 저장소로 옮기기 전의 릴리스는 이전 저장소 gninraw/MediSupport 에 그대로 있습니다 — [v1.0](https://github.com/gninraw/MediSupport/releases/tag/MediChart-KMC-v1.0) · [v1.1](https://github.com/gninraw/MediSupport/releases/tag/MediChart-KMC-v1.1) · [v1.2](https://github.com/gninraw/MediSupport/releases/tag/MediChart-KMC-v1.2).

## 구성

각 릴리스에는 다음 파일이 들어 있습니다.

| 파일 | 내용 |
|---|---|
| `MediChart-KMC-v<버전>.zip` | 연동 자료 전체 — 개발 가이드, `읽어보세요.txt`, `Lib/` · `Demo/` · `Bin/` |
| `MediChart-KMC-EMR-Guide-v<버전>.html` | 개발 가이드(zip 안의 가이드와 같은 파일). 누르시면 내려받기가 되며, 받으신 뒤 브라우저로 여시면 됩니다 |
| `SHA256SUMS.txt` | 위 두 파일의 SHA-256 체크섬 |

Assets 목록 끝의 **Source code (zip)** · **Source code (tar.gz)** 는 GitHub 가 모든 릴리스에 자동으로 붙이는 것으로, 이 README 만 들어 있습니다. 받지 않으셔도 됩니다.

zip 안에는 다음이 들어 있습니다.

| 폴더 · 파일 | 내용 |
|---|---|
| `Lib/` | EMR 프로젝트에 추가하실 라이브러리 소스(`.pas`) |
| `Demo/` | 예제 소스 — `EmrSample.pas` 의 `QueryPrescription` 을 병원 처방 조회로 바꾸시면 됩니다 |
| `Bin/` | 컴파일 없이 확인하실 수 있는 실행 파일 — `MedichartKMC.exe`(연동 시험 화면) · `ConsoleTest.exe`(화면 없이 서버 왕복 확인) · `MedichartKMC.ini`(설정 예시) |
| 개발 가이드 · `읽어보세요.txt` | 빠른 시작, 연동 개발 방법, 참조 규격, 문제 해결 |

## 준비물

- Delphi 7 또는 XE7 (v1.2 는 Delphi 7 에서 컴파일을 확인하였으며, XE7 은 확인 전입니다). 외부 라이브러리가 필요하지 않습니다(Indy · OpenSSL DLL 같은 제3자 라이브러리를 쓰지 않습니다).
- 전송은 Windows 내장 기능(`winhttp.dll`)을 사용하며, HTTPS 로만 연동합니다.

## 빠른 시작

1. zip 을 받아 압축을 풀고, 먼저 개발 가이드와 `읽어보세요.txt` 를 확인 부탁드립니다.
2. `Bin\MedichartKMC.exe` 를 실행해 서버 연결을 확인합니다.
3. 개발 가이드 2장(빠른 시작)을 따라 `Demo\MedichartKMC.dpr` 을 열어 빌드해 봅니다.
4. 개발 가이드 4장(연동 개발)을 참고하여 `EmrSample.pas` 를 병원 처방 조회로 바꿉니다.

Windows 에서 압축을 푸신 뒤 실행 파일을 여실 때 보안 경고가 나오면, 받은 zip 파일의 **속성 › 차단 해제** 를 선택하고 다시 압축을 풀어 주십시오.

## 받은 파일 확인 (선택)

받은 파일과 `SHA256SUMS.txt` 를 같은 폴더에 두고 확인하실 수 있습니다.

- macOS · Linux: `shasum -a 256 -c --ignore-missing SHA256SUMS.txt` (받으신 파일만 확인합니다)
- Windows PowerShell: `Get-FileHash .\MediChart-KMC-v<버전>.zip -Algorithm SHA256` 의 값이 `SHA256SUMS.txt` 와 같은지(대소문자 무시) 확인

## 문의

연동과 관련해 궁금하신 점은 연동 담당자에게 회신해 주시기 바랍니다.
