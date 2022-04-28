---
title:  "[AirSim을 위한 Unreal Engine설치]Thinkpad P15v에 Ubuntu 18.04 설치"
excerpt: " 환경구축을 해보자 "

categories:
  - Blog
tags:
  - [Blog, jekyll, Github, Git]

toc: false
toc_sticky: false
 
date: 2022-04-28
last_modified_at: 2022-04-28
---
# 설치환경
Lenovo ThinkPad P15v Gen2<br>
Intel Core 11세대 i7<br>
Nvidia T1200<br>

#### First trial
- 18.04.6 설치
- 설치 후 부팅 시 "you are in emergency mode" 문구가 뜨며 stuck
> Solution : 레노버 공식 사이트 가이드 따라서 진행
>chrome-extension://efaidnbmnnnibpcajpcglclefindmkaj/https://download.lenovo.com/pccbbs/mobiles_pdf/tp_p15_p17_p1_gen3_ubuntu_20.04_lts_installation_v1.0.pdf

#### Second trial
To get the system boot:
- 위에서 레노버 공식 사이트 가이드 따라한 뒤 18.04.6 설치
- Black Screen에서 stuck
> Solution : https://www.stephenwagner.com/2019/05/05/ubuntu-linux-black-screen-frozen-system-after-upgrade-install/

## Temporary Fix
To get the system to boot:
1. Lenovo 로고가 뜬 부트에서 ESC 눌러 GRUB 진입
2. GRUB에서 "e" key를 누른다
3. "linux" 로 시작하는 라인으로 가서 "ro quiet splash" 라고 적힌 곳을 찾는다
4. "ro quiet splash" 를 "ro quiet splash nomodeset" 으로 수정해준다
5. "F10"을 눌러 재부팅한다.
6. 제대로 부팅이 된다.
## Permanent Fix
To permanently resolve the issue:
1. 위 방법으로 시스템을 부팅시킨다
2. Terminal을 연다
```
cd /etc/default/
sudo nano /grub
```
4. "GRUB_CMDLINE_LINUX_DEFAULT" 변수가 있는 곳으로 이동하여 다음과 같이 수정한다
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```
5. 파일을 저장한다(CTRL+X then press "y")
6. 다음 명령어를 사용하여 grub.conf 파일을 /boot partition에 다시 만들어준다
```
update-grub
```
7. 시스템을 다시 시작한다