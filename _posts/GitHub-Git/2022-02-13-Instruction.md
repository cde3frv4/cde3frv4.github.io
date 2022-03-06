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

##  Git 최초 설정

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
#기본 브랜치 명을 변경한다. 
$ git config --global init.defaultBranch main
# Repository 폴더 만들고, 깃 시작
$ git init
```





## Branch 명령

```bash
#기본 브랜치명을 'main'으로 변경한다. 
git config --global init.defaultBranch main
#로컬 브랜치를 만든다.
git branch (브랜치명)
```

원격 브랜치를 삭제한다. 
```bash
git push origin --delete (브랜치명)
```



```python
git config --global user.name
```

```shell
git config --global user.email
```


### 기본 브랜치명 변경

```shell
git config --global init.defaultBranch main
```

