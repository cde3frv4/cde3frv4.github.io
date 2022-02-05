---
layout: single
title: "글꼴 및 Style 변경"
categories: Blog
toc: true
toc_sticky: true
toc_label: "페이지 주요 목차"
classes: wide

---

## <u>Page 글꼴 및 스타일 바꾸기(인용문 예시) </u>
블로그는 인용문을 할 시 Default된 이탤릭체가 되어있었다. 이를 Normal로 바꿔보고 싶었다. <br>
<blockquote style="font-style: italic">
Before : blockquote Style is Italic
</blockquote>

<blockquote style="font-style: normal">
After : blockquote Style is Italic
</blockquote>

-sass/_pages.scss를 들어가면 .page__content가 나온다.   .page_content는 page에 해당하는 Mark down 글씨체를 바꾸는게 가능하다.  아래와 같이 h1,h2,h3 헤더와 스타일이 먼저 정의되어 있는 것을 볼 수 있다.<br>인용문은 blockquote{}안에  font-style: normal;로 바꿔 인용문의 Default 글씨체를 바꿀 수 있었다. <br>

```scss
.page__content {
 h2 {
    padding-bottom: 0.5em;
    border-bottom: 1px solid $border-color;
 }
 h1, h2, h3, h4, h5, h6 {
   	.header-link {
			position: relative;
			left: 0.5em;
			opacity: 0;
			font-size: 0.8em;
			-webkit-transition: opacity 0.2s ease-in-out 0.1s;
			-moz-transition: opacity 0.2s ease-in-out 0.1s;
			-o-transition: opacity 0.2s ease-in-out 0.1s;
			transition: opacity 0.2s ease-in-out 0.1s;
	}
	&:hover .header-link {
		opacity: 1;
    }
 }    
/*~생략~*/ 

/*[Add]KHK added to not to fix italic*/ 
 blockquote{
   font-style: normal;
 }
}
```

