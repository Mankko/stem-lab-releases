# Stem Lab Releases

Stem Lab의 **공개 Windows 설치파일 배포 전용 저장소**입니다.

현재 최신 배포 버전: **v0.5.6**

소스 코드는 이 저장소에 포함하지 않습니다. 일반 사용자가 설치할 수 있는 Windows 배포본만 GitHub Releases로 제공합니다.

## 다운로드

- 최신 Windows 설치파일: https://github.com/Mankko/stem-lab-releases/releases/latest/download/StemLab-Setup-x64.exe
- 최신 Release 페이지: https://github.com/Mankko/stem-lab-releases/releases/latest
- v0.5.6 설치파일: https://github.com/Mankko/stem-lab-releases/releases/download/v0.5.6/StemLab-Setup-x64.exe

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
- 파트별 Mute / Solo / 볼륨 조절 및 미리듣기
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
