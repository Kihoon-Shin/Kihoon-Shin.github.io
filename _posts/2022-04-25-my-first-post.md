---
title:  "[AirSim을 위한 Unreal Engine설치]Lenovo LEGION 환경설정"
excerpt: "Dual Monitor를 위한 Nvidia-driver를 설치해보자 "

categories:
  - Blog
tags:
  - [Blog, jekyll, Github, Git]

toc: false
toc_sticky: false
 
date: 2022-04-25
last_modified_at: 2022-04-25
---
# 설치환경
Lenovo LEGION<br>
Intel CORE i7<br>
GeForce RTX 3060<br>
Ubuntu 18.04<br>

#### Fist trial
- 18.04.6 설치
- 그래픽카드 정보 및 드라이버 확인

        ubuntu-drivers devices
        // nvidia-driver-470 is recomdmened
- PPA로 470 driver 설치
- 그 결과 Laptop은 부팅 창에서 Stuck되는데(blackscreen), 외부 Display(HDMI)는 연결이 되는 현상 발생

#### Second trial
- 18.04.6 설치
- 그래픽카드 정보 및 드라이버 확인

        ubuntu-drivers devices
        // nvidia-driver-470이 recommended
- Window key -> Software updator로 470 driver 설치
- 그 결과 Laptop은 부팅 창에서 Stuck되는데, 외부 Display(HDMI)는 연결이 되는 현상 발생
> Solution : 아래와 같이 따라하면 된다.
## Install Nvidia Driver on Ubuntu 18.04

### Secure Boot

*This section applies to machines with Secure Boot, such as ThinkPad.*

1. Before installation, switch to "Discrete Graphics" in BIOS, if both Intel and Nvidia graphics are present.
2. During installation, make sure to select the "Install third-party software for graphics and Wi-Fi hardware and addition media formats" in "Updates and other software" screen.
3. Select "Configure Secure Boot", and set password.
4. Continue Ubuntu installation as normal.
5. During the first reboot, "Perform MOK management" screen will showup. Select "Enroll MOK" option.
6. Select "Continue", then, "Yes".
7. "Enroll the key(s)?" screen will present. Enter the password from Step 3.
8. "OK" to reboot.
9. Once login to the Desktop, do the following to update the Nvidia driver.

### Update to latest Nvidia Driver

```sh
## check display card and driver status
sudo lshw -c display
# or sudo lshw -c video

## check loaded display card and driver
lsmod | grep nvidia
# or nvidia-smi
# or lsmod | grep nouveau

## remove old Nvidia driver
sudo apt purge nvidia-*
# or sudo apt remove nvidia-*

## add driver repository
sudo add-apt-repository ppa:graphics-drivers/ppa

## identify suitable driver version
sudo ubuntu-drivers devices
## if ubuntu-drivers command not found
sudo apt install ubuntu-drivers-common

## install drivers from ppa database
sudo apt install nvidia-driver-470

## reboot
sudo reboot

## check driver details and settings
nvidia-smi or nvidia-settings

## select driver
prime-select query
sudo prime-select nvidia or sudo prime-select intel

## display usage
dpkg -L nvidia-driver-470
```

이제 듀얼모니터로 잘 작동한다!
