---
title:  "[AirSim을 위한 Unreal Engine설치]Unreal Engine 설치"
excerpt: " Unreal Engine을 설치해보자 "

categories:
  - Blog
tags:
  - [Blog, jekyll, Github, Git]

toc: false
toc_sticky: false
 
date: 2022-04-25
last_modified_at: 2022-04-25
---
## Unreal Engine 4.5 설치
- Epic Games와 Github 계정 연동해준다.
- Epic Games의 Github에서 Git clone으로 Unreal Engine 다운로드
- ./Setup.sh 실행하니깐 wget으로 Clang Cross Compiler를  받으려하는데 서버가 원할하지 않은지 retry를 20번 시도하고 설치가 불완전하게 종료됨
- ./GenerateFiles.sh 실행 시 많은 Warning 발생
- make 입력 시 에러 발생
> Solution : Github에서 git clone으로 말고 zip파일 다운로드하여 위와같은 방식으로 설치
- 4.5 버전이 아닌 realease로 설치하였더니 UnrealEditor가 5.0버전으로 설치됨. 
- AirSim을 Build하는 과정에서 버전이 맞지 않다는 에러 발생