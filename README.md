# Stem Lab Releases

Stem Lab의 **공개 Windows 설치파일 배포 전용 저장소**입니다.

소스 코드는 이 저장소에 포함하지 않습니다. 이 저장소에는 일반 사용자가 설치할 수 있는 Windows 배포본만 GitHub Releases로 제공합니다.

## 다운로드

- 최신 Windows 설치파일: https://github.com/Mankko/stem-lab-releases/releases/latest/download/StemLab-Setup-x64.exe
- 최신 Release 페이지: https://github.com/Mankko/stem-lab-releases/releases/latest

## 자동 업데이트

Stem Lab v0.5.0부터 프로그램 시작 시 이 저장소의 최신 Release를 자동으로 확인합니다. 현재 설치된 버전보다 새 Release가 있으면 업데이트 안내창을 표시하고, 사용자가 선택하면 해당 Release의 `StemLab-Setup-x64.exe` 다운로드를 엽니다.

새 버전 배포 시에는 최신 Release에 아래 이름의 설치파일 Asset이 반드시 존재해야 합니다.

```text
StemLab-Setup-x64.exe
```

## 배포 형식

- 파일명: `StemLab-Setup-x64.exe`
- 지원 OS: Windows 10/11 64-bit
- Python 별도 설치 불필요
- NVIDIA GPU가 감지되면 CUDA 모드를 사용하고, NVIDIA GPU가 없으면 CPU 모드로 동작합니다.
- 대용량 AI 런타임과 모델은 설치파일에 포함하지 않으며 최초 사용 시 필요한 구성요소를 자동으로 다운로드합니다.

## 저장소 용도

이 저장소는 설치파일 배포 전용입니다. 개발 소스, 내부 빌드 스크립트, 테스트 코드 및 작업 문서는 별도의 private 소스 저장소에서 관리합니다.
