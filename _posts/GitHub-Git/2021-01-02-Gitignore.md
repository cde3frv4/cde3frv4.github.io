---
layout: single
title: "[Git] Gitignore"
categories: Git
toc: true
toc_sticky: true
toc_label: "주요 목차"
#classes: wide
author_profile: true
sidebar:
nav: main
#published: false
---
##  1 .gitignore 사용 및 설명
프로젝트를 하다보면 Password 등 프로젝트에서 업로드 자동제외 시키기 위해 .gitignore 파일을 사용한다.   
아래와 같이 password.yaml 파일 추가 생성해보자. 

### password.yaml 생성 

```yaml
Id: Admin
PW: 123456789
```



또한 .gitignore 파일을 만들고, 거기에 password.yaml를 입력해보자. 아래와 같이 지난 시간에 만든 A.yaml을 포함한 총 3개의 파일이 있다. 그리고 .gitignore파일에 password.yaml을 추가하면, 프로젝트에서 제외되어 VS Code 비실행표시를 나타낸다.
<img src="/assets\images\GitHub\Git\2_GitIgnore\Files.png" style="zoom:%100;" >


##  2 .gitignore 등록 형식
.gitignore는 다음과 같은 규칙으로 등록가능하다. 

```bash
# 이렇게 #를 사용해서 주석
# 모든 file.c
file.c

# 최상위 폴더의 file.c
/file.c

# 모든 .c 확장자 파일
*.c

# .c 확장자지만 무시하지 않을 파일
!not_ignore_this.c

# logs란 이름의 파일 또는 폴더와 그 내용들
logs

# logs란 이름의 폴더와 그 내용들
logs/

# 현재 폴더 안에 logs란 이름의 폴더와 그 내용들
/logs/

# logs 폴더 바로 안의 debug.log와 .c 파일들
logs/debug.log
logs/*.c

# logs 폴더 바로 안, 또는 그 안의 다른 폴더(들) 안의 debug.log
logs/**/debug.log
```

