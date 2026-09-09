# Stem Lab Releases

Stem Lab의 **공개 Windows 설치파일 배포 전용 저장소**입니다.

현재 최신 배포 버전: **v0.5.3**

소스 코드는 이 저장소에 포함하지 않습니다. 일반 사용자가 설치할 수 있는 Windows 배포본만 GitHub Releases로 제공합니다.

## 다운로드

- 최신 Windows 설치파일: https://github.com/Mankko/stem-lab-releases/releases/latest/download/StemLab-Setup-x64.exe
- 최신 Release 페이지: https://github.com/Mankko/stem-lab-releases/releases/latest
- v0.5.3 설치파일: https://github.com/Mankko/stem-lab-releases/releases/download/v0.5.3/StemLab-Setup-x64.exe

## v0.5.3 주요 기능

- 메인 화면과 Windows 창 제목에서 현재 설치 버전 확인
- 실행 중인 Stem Lab 창과 작업표시줄에 전용 앱 아이콘 적용
- 업데이트 버튼을 `업데이트 다운로드 후 종료`로 변경
- 업데이트 다운로드 주소를 연 뒤 현재 Stem Lab 자동 종료
- 파트 분리/분석/보컬 추가 분리/Key 변경 작업 중에는 업데이트 안내를 작업 완료 후 표시

## v0.5.2 주요 수정

- 최초 BPM/Key 분석 완료 후에도 `재생 속도 / BPM 변경 사용` 체크박스가 비활성화 상태로 남던 문제 수정

## v0.5.1 주요 기능

- 재생 속도 / 목표 BPM 변경
- 지원 범위 50% ~ 150%
- 속도 입력과 목표 BPM 입력 양방향 연동
- FFmpeg `atempo` 기반으로 Tempo를 바꾸면서 음악적 Key 유지
- 변경된 Tempo를 미리듣기와 WAV/MP3 저장에 동일 적용
- 기존 Key 변경 기능과 함께 사용 가능

## 자동 업데이트

Stem Lab v0.5.0부터 프로그램 시작 시 이 저장소의 최신 Release를 자동으로 확인합니다. 현재 설치된 버전보다 새 Release가 있으면 업데이트 안내창을 표시합니다.

v0.5.3부터 `업데이트 다운로드 후 종료`를 선택하면 최신 `StemLab-Setup-x64.exe` 다운로드 주소를 기본 브라우저에서 연 뒤 현재 Stem Lab을 종료합니다. 백그라운드 음원 작업이 진행 중인 경우에는 업데이트 안내를 즉시 띄우지 않고 작업 완료 후 표시합니다.

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
