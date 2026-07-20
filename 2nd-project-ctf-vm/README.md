# EasyHajo CTF VM

2차 프로젝트 기간에 HRSMS와는 별도로, 팀에서 자체 제작한 CTF 취약 VM 머신입니다.
난이도: 쉬움(Easy)~보통(Medium) · 분야: 웹 해킹(Web Hacking), 권한 상승(Privilege Escalation)

웹 애플리케이션의 설정 오류와 파일 시스템 보안 미비를 통해 초기 침투부터 루트 권한 획득까지 경험하는 다단계 시나리오로 설계했습니다.

## 구성

- `src/` — 취약점이 삽입된 서비스 소스 코드 및 환경 구축 스크립트
- `writeup/` — 문제 풀이 워크스루 (PDF)

## 취약점 개요

| 단계 | 목표 | 핵심 기법 |
|---|---|---|
| 1 | 초기 정찰 | 포트 스캔(nmap) 및 디렉토리 브루트 포싱(gobuster) |
| 2 | 소스 코드 분석 | 백업 파일(`*.bak`) 노출을 통한 인증 로직 우회 |
| 3 | 초기 침투 | 쿠키 검증 우회(Burp Suite Intruder) + 파일 업로드 취약점 → 리버스 쉘 |
| 4 | 내부 정찰 | 커맨드 인젝션(OS Command Injection)을 통한 내부 정보 수집 |
| 5 | 권한 상승 | `sudo NOPASSWD` 오설정 스크립트를 이용한 커맨드 인젝션 → 루트 쉘 |

## VM 이미지

VM 전체 이미지(.ova, 약 1.5GB)는 용량 문제로 이 저장소에는 포함하지 않았습니다.
아래 링크에서 다운로드해 VMware/VirtualBox로 import해서 실행하세요.

- 다운로드: <!-- 구글드라이브 등 업로드 후 링크 채우기 -->

## 실행 방법

1. 위 링크에서 `.ova` 파일을 받아 VirtualBox/VMware에서 Import
2. NAT 또는 브리지 네트워크로 설정 후 VM 부팅
3. 자세한 공략 과정은 [`writeup/Easyhajo_walkthrough.pdf`](./writeup/Easyhajo_walkthrough.pdf), 출제 배경은 [`writeup/EasyhajoCTF 문제 출제 의도.pdf`](./writeup/EasyhajoCTF%20문제%20출제%20의도.pdf) 참고
