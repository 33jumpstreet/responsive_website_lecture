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
```
.title .btn:hover {
  box-shadow: 
    0 0 0 3px rgba(71, 154, 191, 0.9) inset,
    0 0 0 100px rgba(0, 0, 0, 0.1) inset;
}
```

