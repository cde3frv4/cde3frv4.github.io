---
layout: single
title: "[Git] Instruction(전체요약)주요 명령어"
categories: Git
toc: true
toc_sticky: true
toc_label: "주요 목차"
classes: wide
author_profile: true
sidebar:
nav: main
#published: fals
---

## 1.Git 최초 설정

```bash
#최신 버전을 확인한다.
$ git version
git version 2.31.1.windows.1

#터미널 프로그램에서 이름/메일을 설정한다.
$ git config --global user.name "HansKim"
$ git config --global user.email "abcd@gmail.com"

#터미널 프로그램에서 이름/메일 확인한다. 
$ git config --global user.name
HansKim
$ git config --global user.email
abcd@gmail.com
```

```bash
#기본 브랜치 명을 변경. 
$ git config --global init.defaultBranch main
# Repository 폴더 만들고, 깃 시작
$ git init
```

## 2. status/ add/ commit 명령

```bash
#상태 확인
$ git status
#특정 파일을 담는다. 
$ git add A.yaml
#모든 파일을 담는다. 
$ git add .
#hunk별 스테이징 진행
$ git add -p
#변경사항 확인하고, 커밋
$ git commit -v
```

##  3. Reset/Revert 명령

```bash
$ git reset --soft b6867ad
$ git reset --mixed b6867ad
$ git reset --hard b6867ad

$ git revert 4323d18
```

## 4.원하는  위치 HEAD 이동

```bash
$ git checkout HEAD~
$ git checkout b6867ad
```



## 5.Branch 명령

```bash
#기본 브랜치명을 'main'으로 변경한다. 
$ git config --global init.defaultBranch main
#로컬 브랜치를 만든다.
$ $ git branch (브랜치명)
#모든 브랜치를 본다.
$ git branch -a
```

### 원격 브랜치 제어

```bash
#원격의 브랜치를 가져와 동일한 이름 로컬 브랜치 만듬
$ git checkout origin/(브랜치명)
$ git switch -t origin/(브랜치명)
#원격의 브랜치 삭제
$ git push origin --delete (브랜치명)
```

## 7.HELP 및 기타 옵션

```bash
#기본적인 명령어들과 설명
$ git help
#Git의 모든 명령어들
$ git help -a
#해당 명령어의 설명과 옵션 보기
$ git (명령어) -h
```



```shell
#현재 모든 설정값 보기
$ git config --list
$ git config --global --list
#에디터에서 보기 (기본: vi)
$ git config (global) -e
#기본 에디터 수정
$ git config --global core.editor "code --wait"
#단축키 수정
$ git config --global alias.(단축키) "명령어"
> $ git config --global alias.cam "commit -am"
#줄바꿈 호환 문제 해결
$ git config --global core.autocrlf (윈도우: true / 맥: input)
#기본브랜치명 변경
$ git config --global init.defaultBranch main
```

