---
layout: single
title: "Markdown기본문법 요약"
categories: GitBlog
toc: true
toc_sticky: true
toc_label: "페이지 주요 목차"
classes: wide

---

## <u>줄/문단</u>
### @줄바꾸기
**방법1.  문장 뒤에 스페이스바를 두번 + Enter 해준다.**  
**방법2. \<br> 또한 줄바꿈을 해주는 HTML 태그이다.**

안녕하세요.   
저는 한스킴이라고, 합니다.

<br>
안녕하세요.<br>
저는 한스킴이라고 합니다.

### @문단 나누기
**두줄을 띄어쓰기 진행**

안녕하세요. 

한스킴이라고 합니다. 

## <u>중첩된 구조</u>
**중첩된 구조를 만드려면 두번째 줄을 스페이스바 2번 후 - . 세번째 줄은스페이스바 4번 후 -**
```
- 1th  
  - 2th  
    - 3th  
```
- 1th  
  - 2th  
    - 3th  

## <u>글꼴</u>
### @강조
```  
**강조된 텍스트입니다**  
```  
강조된 텍스트입니다

### @글씨색
```  
<span style="color:yellow">노란 글씨입니다.</span>
```    
<span style="color:yellow">노란 글씨입니다.</span>

## <u>링크</u>
### @일반링크
```
<https://www.naver.com>
```
<https://www.naver.com>

### @설명이 있는링크
```
[네이버 홈페이지](https://www.naver.com)
```
[네이버 홈페이지](https://www.naver.com)


### @이미지 링크
**방법1.HTML 방식**  
\<center></center> 는 중앙정렬이다. 또한 width, height를 써서 그림 크기 조정가능
```
<center>
    <img src="https://i.esdrop.com/d/ZklKfna5T3.jpg" title="하얀 강아지" width="100%">
    <figcaption>하얀 강아지</figcaption>
</center>  
```
<center>
    <img src="https://i.esdrop.com/d/ZklKfna5T3.jpg" title="하얀 강아지" width="100%">
    <figcaption>하얀 강아지</figcaption>
</center>  
  
**방법2.일반 방식**  
```
![하얀 강아지](https://i.esdrop.com/d/ZklKfna5T3.jpg "하얀 강아지")
```

</figure>
## <u>참조레퍼런스</u>
<https://github-wiki-see.page/m/gnuoynawh/wiki/wiki/%EB%A7%88%ED%81%AC%EB%8B%A4%EC%9A%B4-%EB%AC%B8%EB%B2%95-(MarkDown-Syntax)#5.-%EB%A7%81%ED%81%AC-links>