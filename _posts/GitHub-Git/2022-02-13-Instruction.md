---
layout: single
title: "[Git]주요 명령어"
categories: Git
toc: true
toc_sticky: true
toc_label: "페이지 주요 목차"
classes: wide
author_profile: true
sidebar:
nav: main
#published: false
---



## 1.Branch 관련명령

로컬 브랜치를 만든다. 
```shell
git branch (브랜치명)
```

원격 브랜치를 삭제한다. 
```shell
git push origin --delete (브랜치명)
```



```shell
git config --global user.name
```

```shell
git config --global user.email
```


### 기본 브랜치명 변경

```shell
git config --global init.defaultBranch main
```


## 2. 프로젝트 생성 & Git 관리 시작

적당한 위치에 원하는 이름으로 폴더를 생성하고 **VS Code**로 열람

해당 폴더에서(VS Code 터미널 기본) 아래 명령어 입력

```
git init
```


폴더에 숨김모드로 **.git** 폴더 생성 확인

- 🛑 이 폴더를 지우면 Git 관리내역이 삭제됩니다. (현 파일들은 유지)
- 맥에서 숨김 파일 보기: `command` + `shift` + `.`

아래의 파일들 생성

*tigers.yaml*

```yaml
team: Tigers
manager: John
members:
- Linda
- William
- David
```

*lions.yaml*

```yaml
team: Lions
manager: Mary
members:
- Thomas
- Karen
- Margaret
```

### ❗️ 모든 작업(파일 생성, 수정)마다 파일을 꼭 **저장**

터미널에 아래 명령어 입력

```
git status
```


## 3. 소스트리로 해보기

### 현존하는 저장소 추가

- 소스트리에 폴더를 드래그하거나, `로컬 저장소 추가`


### Git이 관리하는 저장소 새로 만들기

- .git 폴더 삭제 후 진행
- 소스트리에 폴더를 드래그하거나, `로컬 저장소 생성`