---
layout: single
title: "[Git] Reset_Revert, 과거로 되돌아가기"
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

## 1.Hash?

해시값은 아래와 같이 커밋 번호를 의미한다. 해당 커밋 번호로 변경 위치를 추적한다.
<img src="/assets\images\GitHub\Git\4_Reset_Revert\Hash.png" style="zoom:%100;" >

## 2 . Reset

Reset은 커밋 내역을 없애고, 되돌린다. 


### git reset  --soft  (해시값) : 로컬 유지, staged가 됨
```bash
cde3f@DESKTOP-UROKU57 MINGW64 /d/Github/Git_Test (main)
$ git reset --soft b6867ad
```

### git reset  --mixed  (해시값) : 로컬 유지, staged가 안됨
```bash
cde3f@DESKTOP-UROKU57 MINGW64 /d/Github/Git_Test (main)
$ git reset --mixed b6867ad
Unstaged changes after reset:
M       B.yaml

```

### git reset  --hard (해시값) : 로컬 내용을 변경하여 해당 해시 커밋으로 간다. 
```bash
cde3f@DESKTOP-UROKU57 MINGW64 /d/Github/Git_Test (main)
$ git reset --hard b6867ad
HEAD is now at b6867ad Add Class B
```

<span style="color:red">  ※주의) --hard는 로컬의 변경 사항을 변경하니 사용 시 각별히 주의한다.</span>

<img src="/assets\images\GitHub\Git\4_Reset_Revert\Reset(mixed_softed).png" style="zoom:%100;" >

<img src="/assets\images\GitHub\Git\4_Reset_Revert\Reset(hard).png" style="zoom:%80;" >



## 3 . Revert

Revert는 커밋 내역을 유지한채 되돌린다.  즉 중간에 수정한 내용을 뺄 때 유용하게 쓰인다.  
아래와 같이 A에 Kim을  추가한 내역을 되돌리는  걸 Revert로 해보자  
<img src="/assets\images\GitHub\Git\4_Reset_Revert\Revert_ex.png" style="zoom:%80;" >

### git revert  (해시값) : revert  후  커밋완료됨
```bash
cde3f@DESKTOP-UROKU57 MINGW64 /d/Github/Git_Test (main)
$ git revert 4323d18
[main 3b74348] Revert "Add Kim in A"
                                     1 file changed, 1 insertion(+), 2 deletions(-)
```
아래와 같이 revert 시 나올 수 있다. esc를 누르고 :wq를 누르면 revert 커밋이 적용된다.   
```bash
mRevert "Add Kim in A"

This reverts commit 4323d186f98c1b3daa592e00d38d7de1e024f2c3.

# Please enter the commit message for your changes. Lines starting
# with '#' will be ignored, and an empty message aborts the commit.
#
# On branch main
# Changes to be committed:
#       modified:   A.yaml
```

### git revert --no-commit (해시값) : 커밋 없이 되돌리기  
```bash
cde3f@DESKTOP-UROKU57 MINGW64 /d/Github/Git_Test (main)
$ git revert --no-commit 4323d18

```

