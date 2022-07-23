# 반응형 웹 사이트 만들기

> 웹스토리보이님의 유튜브 강의를 보며 실습하였습니다. 

### 1. 시맨틱 태그
- 정의   
\- 의미를 부여하고 그 의미에 맞는 태그를 시작하기 위해 사용  
\- 시맨틱 태그를 사용하면, 자동으로 웹 표준까지 준수하게 되기 때문에 시맨틱 태그 쓰는 것을 권장  

- 장점    
\- 웹 표준 및 접근성 향상   
\- 검색 엔진 최적화(SEO)  
\- 유지 보수 용이성 
***  
### 2. 미디어 쿼리 
- 정의
\- 화면 크기에 따른 각각의 속성 값을 지정하여, 여러가지 화면을 구성하는 기술
\- 단말기의 유형(출력물 vs. 화면)과, 어떤 특성이나 수치(화면 해상도, 뷰포트 너비 등)에 따라 웹 사이트나 앱의 스타일을 수정할 때 유용 

- 사용방법 
```
/* 화면 너비 0 ~ 1220px */
@media (max-width: 1220px) {
  .container {
    width: 100%;
  }
}
```
***
### 3. 아이콘 사용하기 - fontawesome  
- fontawesome에서 아이콘을 가져와서 사용 (예전 버전인 4.7 이용)  
https://fontawesome.bootstrapcheatsheets.com/#  

***

### 4. 메타 태그 - 페이스북, 트위터 
- 정의  
\- 웹 서버와 웹 브라우저간에 상호 교환되는 정보를 정의하는데 사용  
\- <head> 태그에 입력하는 태그로, 사이트의 디자인에는 영향을 미치지 않고, 문서가 어떤 내용을 담고 있고, 문서의 키워드는 무엇이며, 누가 만들었는지 등의 문서 자체의 특성을 담고 있습니다.   
\- 페이스북이나 트위터에 url을 공유하면 대표이미지와 제목, 내용 등이 보이게 된다. 

- 사용 방법  
```
  <!-- !-- Facebook meta tags -->
  <meta property="og:type" content="article" />
  <meta property="og:title" content="반응형 사이트 만들기(title)" />
  <meta property="og:url" content="http://richclub8.dothome.co.kr/responsive/html5/index.html" />
  <meta property="og:image" content="http://richclub8.dothome.co.kr/assets/ico/icon.png" />
  <meta property="og:site_name" content="반응형 사이트 만들기(site_name)" />
  <meta property="og:description" content="반응형 사이트 따라하기(description)" />

  <!-- twitter meta tags -->
  <meta name="twitter:card" content="summary_large_image" />
  <meta name="twitter:site" content="@padakmon" />
  <meta name="twitter:title" content="반응형 사이트 만들기(title)" />
  <meta name="twitter:description" content="반응형 사이트 만들기(description)." />
  <meta property="twitter:image" content="http://richclub8.dothome.co.kr/assets/ico/icon.png" />
```
***
### 5. 마우스 오버시 box-shadow로 효과 주기
- box-shadow 속성은 박스 요소의 그림자를 설정  
- 사용방법  
```
.title .btn:hover {
  box-shadow: 
    0 0 0 3px rgba(71, 154, 191, 0.9) inset,
    0 0 0 100px rgba(0, 0, 0, 0.1) inset;
}
``` 
---
### 6 한줄 효과  
```
overflow: hidden;
text-overflow: ellipsis;
white-space: nowrap;
```
---
### 7. 두줄 효과
```
overflow: hidden;
text-overflow: ellipsis;
display: -webkit-box;
-webkit-box-orient: vertical;
-webkit-line-clamp: 2; // 단점: ie 지원을 안함. 
max-height: 40px; /* ie에서도 두줄로 보이도록 따로 설정 */ 
```
---
### 8. 반응형에서 이미지를 표현하는 방법  
- 기기에 따라 단지 크기만 다른, 동일한 이미지 콘텐츠를 보여 주고 싶을 때 사용  
- (1) srcset 설정  
\- srcset은 브라우저에게 제시할 이미지 목록과 그 크기를 정의한다. 각 쉼표 앞에 이렇게 적는다.  
\- 1) 이미지 파일명 (img/blog2_@1.jpg img/blog2_@2.jpg)  
\- 2) 공백  
\- 3) 이미지 고유 픽셀 너비 (1x 2x) 
  여기서는 레티나를 사용했는데, 레티나는 픽셀이 보통의 2배 이상의 꽉 찬 이미지리라고 생각을 하면된다. 
  즉, 물리적으로 같은 폭이라 해도 픽셀을 2배로 채우는 것이다. 
  
``` 
<img src="img/blog2_@1.jpg" srcset="img/blog2_@1.jpg 1x, img/blog2_@2.jpg 2x" alt="normal image">
```
- (2) 미디어 쿼리를 사용한 방법 

```
// html
<img src="img/blog1_@1.jpg" class="img-normal" alt="normal image">
<img src="img/blog1_@2.jpg" class="img-retina" alt="retina image" width="100%">

// css
.blog1 img {
  width: 100%;
}
.blog1 .img-retina {
  display: none;
}

@media only screen and (-webkit-min-device-pixel-ratio: 1.5),
only screen and (min-device-pixel-ratio: 1.5),
only screen and (min-resolution: 1.5dppx) {
    .blog1 .img-retina {display: initial;}
    .blog1 .img-normal {display: none;}
}

```
  
> 참고 사이트 
- mdn 문서 반응형 이미지 관련 설명   
https://developer.mozilla.org/ko/docs/Learn/HTML/Multimedia_and_embedding/Responsive_images#%EB%8D%94_%EC%95%8C%EC%95%84_%EB%B3%B4%EA%B8%B0  
- 개인블로그 srcset과 sizes 설명  
https://codingcoding.tistory.com/386  
- 레티나 설명  
https://kangraemin.github.io/ios/2021/01/21/iOS-image-set/
  
---
### 9. slick을 이용한 이미지 슬라이더 구현 
> 참고 사이트   
https://kenwheeler.github.io/slick/  
---
### 10. lightgalleryjs를 이용한 갤러리 슬라이더 구현
> 참고사이트   
https://www.lightgalleryjs.com/docs/settings/  
---
### 11. filter로 이미지 보정하기 
- 포토샵에서 사진을 보정하는 것처럼 css에서도 보정이 가능
- 사용방법
```
filter: blur(5px);
filter: brightness(0.4);
filter: contrast(200%);
filter: drop-shadow(16px 16px 20px blue);
filter: grayscale(50%);
filter: hue-rotate(90deg);
filter: invert(75%);
filter: opacity(25%);
filter: saturate(30%);
filter: sepia(60%);
```
> 참고 사이트 MDN 문서  
https://developer.mozilla.org/ko/docs/Web/CSS/filter
---
### 12. JS로 접고/ 펼칠 수 있는 기능 구현 
```
$(".btn").click(function(e){
  e.preventDefault(); // 상단으로 올라가는 현상 제어
  $(".nav").slideToggle(); // nav 클래스가 슬라이드 토글
  $(".btn").toggleClass("open"); // .btn 클래스에 open 이라는 토글 클래스를 추가

  if($(".btn").hasClass("open")) { // if문을 사용, 조건: open 클래스 명이 있을 때
    // open이 있을 때
    $(".btn").find("i").attr("class", 'fa fa-angle-up'); // btn 클래스에서 i 태그를 찾아서 클래스에 속성값을 부여
  } else {
    // open이 없을 때
    $(".btn").find("i").attr("class", 'fa fa-angle-down'); // open 클래스가 없다면, btn 클래스에서 i 태그를 찾아서 클래스에 속성값을 부여
  }
});

// 반응형 구현 
$(window).resize(function(){ 
  var wWidth = $(window).width();
  if(wWidth > 600) {
    $(".nav").removeAttr("style");
  }
});  
```
---  
  
  
