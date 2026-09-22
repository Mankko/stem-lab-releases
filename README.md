# Stem Lab Releases

Stem Lab의 **공개 Windows 설치파일 배포 전용 저장소**입니다.

현재 최신 배포 버전: **v0.8.7**

소스 코드는 이 저장소에 포함하지 않습니다. 일반 사용자가 설치할 수 있는 Windows 배포본만 GitHub Releases로 제공합니다.

## 다운로드

- 최신 Windows 설치파일: https://github.com/Mankko/stem-lab-releases/releases/latest/download/StemLab-Setup-x64.exe
- 최신 Release 페이지: https://github.com/Mankko/stem-lab-releases/releases/latest
- v0.8.7 설치파일: https://github.com/Mankko/stem-lab-releases/releases/download/v0.8.7/StemLab-Setup-x64.exe

## v0.8.7 수정사항

- YouTube 오디오 가져오기 첫 시도는 yt-dlp 기본 네트워크 정책을 유지하고, 일시 오류 재시도에서만 IPv4 fallback 적용
- Windows 배율/폰트 크기 조합에서 첫 번째 탭의 GroupBox와 입력 필드가 세로로 눌리며 겹치던 UI 문제 수정
- 노래 선택/파트 나누기 탭을 DPI-aware 최소 높이로 유지
- 창 높이가 부족한 경우 내부 컨트롤을 압축하지 않고 세로 스크롤로 전환
- 노래 선택/분리 설정 GroupBox가 자연 높이 이하로 줄어들지 않도록 보호

## v0.8.6 수정사항

- v0.8.5에서 남아 있던 Windows 오류 448 재발 문제 수정
- uv가 만든 venv의 `Scripts\\python.exe`가 reparse/junction 경로가 되어 차단되는 환경을 우회
- Demucs 및 코드악보 런타임 생성 시 `uv venv` 대신 실제 CPython으로 `python -m venv --copies --without-pip` 사용
- venv 내부 Python 실행 파일을 실제 복사 파일로 만들어 `STATUS_UNTRUSTED_MOUNT_POINT` 경로를 제거
- Demucs/Chord runtime revision을 올려 기존 손상된 venv를 자동 재생성

## v0.8.5 수정사항

- Windows 일부 환경에서 uv가 Python 3.12 다운로드 후 minor-version junction 생성 중 오류 코드 448로 실패하던 문제 우회
- `cpython-3.12.x-windows-x86_64-none\\python.exe` 실제 patch interpreter를 직접 탐색해 사용
- 깨진 `cpython-3.12-windows-x86_64-none` junction이 남아 있어도 Demucs/코드악보/보컬 런타임 구성이 계속 진행되도록 보강
- 이후 uv venv/tool 호출에는 `3.12` 별칭 대신 실제 Python 실행 파일 절대 경로 전달

## v0.8.4 수정사항

- YouTube 오디오 가져오기 중 HTTP 403/408/425/429/5xx 및 일시적 네트워크 오류 자동 재시도
- 최대 3회까지 새 yt-dlp 세션으로 원본 URL부터 다시 추출
- yt-dlp 내부 retries / fragment_retries / extractor_retries 및 socket timeout 적용
- 실패 시도별 임시 다운로드 파일 격리/정리
- 자동 재시도 로그 한국어 / English 지원
- Windows 선택 코드칸 화살표 caret 동작 안정화
- 전체 회귀 테스트 199개 통과 및 Windows 패키징 검증 완료

## v0.8.3 수정사항

- 코드악보 BPM 직접 입력 시 소수점 이하 값이 되돌아가던 문제 수정
- BPM 위/아래 버튼 0.1 BPM 증감값이 Tempo 퍼센트 반올림으로 변형되던 문제 수정
- 코드악보 BPM 적용 중 playback/tempo 역방향 동기화 차단
- 실제 playback/export tempo rate를 정확한 target BPM 기준으로 계산
- 관련 회귀 테스트 추가 및 197 tests 통과

## v0.8.2 수정사항

- 메인 창 최소 크기를 1200x800으로 상향해 Windows 배율 환경에서 입력 영역이 눌리는 현상 완화
- 코드악보 생성 시 primary lv-chordia worker가 Windows Terminal 창을 띄우지 않도록 `CREATE_NO_WINDOW` 적용
- 관련 회귀 테스트 추가

## v0.8.1 수정사항

- Windows 설치본에서 누락됐던 lv-chordia worker 파일 포함
- 코드악보 최초 사용 시 전용 lv-chordia / Beat This CPU 런타임 자동 구성
- fallback 코드 분석에도 곡 정보 분석 Key 전달
- 코드악보 Original Key가 곡 정보 분석 Key를 기준으로 유지되도록 수정
- Windows frozen smoke test에 chord worker 존재 여부 검증 추가

## v0.8.0 주요 기능

- 코드악보 인식 정확도와 리듬 정렬 개선
  - Beat This 기반 beat/downbeat 추적
  - lv-chordia 기반 코드 인식 및 보조 ensemble
  - 0.5박 단위 코드 위치 표현
  - Slash chord / 확장 코드 / Key 기준 enharmonic spelling 보강
- 코드악보 편집 기능 강화
  - 코드 직접 수정
  - 마디 추가 / 삭제
  - 수동 가사 입력
  - Undo / Redo
  - 방향키 코드칸 이동
  - 화면 폭에 따른 코드 폰트 자동 조절
- Player 연동
  - 재생 중 현재 마디 강조
  - 현재 마디 자동 스크롤
  - 코드 클릭은 편집 전용으로 유지
- 코드악보 표시 설정
  - BPM 직접 수정
  - 코드악보 전용 Key 변경 `-6 ~ +6`
  - 1반음 단위 조절
  - 저장 악보의 BPM / Key 상태 복원
- 저장 악보 관리
  - 새 악보 저장
  - 기존 악보 덮어쓰기
  - 다른 이름으로 저장
  - 저장 악보 삭제
- 출력
  - A4 인쇄 미리보기
  - PDF 저장
  - 제목 / BPM / Key / 박자표 / 코드 / 가사 출력
- 자동 가사 인식은 제거하고 가사는 코드악보에서 직접 입력하는 방식으로 정리
- 한국어 / English UI 유지
- 전체 회귀 테스트 및 Windows 패키징 검증 완료

## v0.6.0 주요 기능

- 메인 화면의 인라인 미리듣기 컨트롤을 별도 `Stem Lab Player` 창으로 분리
- Player에서 재생 / 일시정지·계속 / 정지 / 탐색(Seek) 지원
- 현재 Preview 선택, Mute/Solo, Stem별 볼륨, Key 변경, Tempo/BPM 변경 상태를 Player 재생에 반영
- 재생 전에 현재 유효 BPM에 맞춘 4박 Count-in 추가
- Count-in은 기본 ON이며 4박 종료 후 음악 자동 시작
- Tempo 변경 사용 시 Target BPM을 Count-in 기준으로 사용
- Count-in 중 Pause/Resume/Stop 지원
- 한국어 / English Player UI 지원
- Player / Count-in 회귀 테스트 및 Windows 패키징 검증 완료

## v0.5.7 주요 수정

- `Start Stem Separation` 버튼과 하단 경계선이 붙어 보이던 UI 여백 문제 수정
- 분리 후 BPM / Key 분석이 완료되어도 `Enable Playback Speed / BPM Change`가 비활성 상태로 남던 문제 수정
- Stem 분리, BPM / Key 분석, 선택적 보컬 추가 분리가 모두 끝난 뒤 완료 안내창이 안정적으로 표시되도록 수정
- BPM / Key 완료 메시지 처리 중 Key 값 포맷 충돌로 후처리가 중단될 수 있던 문제 수정
- English UI의 상단 초기화 버튼을 `Start Over`에서 `Reset`으로 변경
- 관련 UI 및 완료 처리 회귀 테스트 추가

## v0.5.6 주요 개선

- 설치 프로그램에서 한국어 / English 선택 가능
- 설치 시 선택한 언어를 Stem Lab 앱 언어로 그대로 사용
- 업데이트 설치 시 기존 설치 언어를 유지하도록 처리
- 기본 화면뿐 아니라 구간 추출, Tempo/BPM, 진행 상태, 오류 메시지, 업데이트 안내 등 사용자 노출 문자열의 한국어/영어 지원 정리
- 번역 카탈로그 키/placeholder 및 English 번역 잔여 한글 검증 테스트 추가
- 한국어/English Main Window UI smoke test 추가
- Windows 설치파일을 실제 생성하는 Source Quality 검증 Workflow 추가
- 검증 Workflow는 설치파일을 Actions Artifact나 Release로 저장하지 않아 GitHub 저장공간을 중복 사용하지 않음

## 기존 주요 기능

- 특정 구간 추출의 시작/종료 시간을 각각 선택적으로 입력 가능
- Demucs 4/6 파트 분리
- Lead / Backing Vocal 추가 분리
- BPM / Key 분석
- 반주 Key 변경
- 재생 속도 / 목표 BPM 변경 50% ~ 150%
- 파트별 Mute / Solo / 볼륨 조절
- 별도 Player 미리듣기 및 4박 Count-in
- WAV 24-bit / MP3 320 kbps 저장
- NVIDIA CUDA 자동 감지
- 프로그램 시작 시 최신 버전 자동 확인
- 현재 설치 버전 표시 및 Stem Lab 전용 앱 아이콘

## 자동 업데이트

Stem Lab v0.5.0부터 프로그램 시작 시 이 저장소의 최신 Release를 자동으로 확인합니다. 현재 설치된 버전보다 새 Release가 있으면 업데이트 안내창을 표시합니다.

v0.5.3부터 `업데이트 다운로드 후 종료`를 선택하면 최신 `StemLab-Setup-x64.exe` 다운로드 주소를 기본 브라우저에서 연 뒤 현재 Stem Lab을 종료합니다. 백그라운드 음원 작업이 진행 중인 경우에는 업데이트 안내를 작업 완료 후 표시합니다.

새 버전 배포 시 최신 Release에는 반드시 아래 이름의 설치파일 Asset이 존재해야 합니다.

```text
StemLab-Setup-x64.exe
```

## 배포 형식

- 파일명: `StemLab-Setup-x64.exe`
- 지원 OS: Windows 10/11 64-bit
- Python 별도 설치 불필요
- NVIDIA GPU 감지 시 CUDA 모드 사용
- NVIDIA GPU가 없으면 CPU 모드 사용
- 대용량 AI 런타임과 모델은 설치파일에 포함하지 않고 최초 사용 시 필요한 구성요소를 자동 다운로드

## 저장소 용도

이 저장소는 설치파일 배포 전용입니다. 개발 소스, 내부 빌드 스크립트, 테스트 코드 및 작업 문서는 별도의 private 소스 저장소에서 관리합니다.
