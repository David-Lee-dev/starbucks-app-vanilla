# starbucks-app

> 스타벅스 웹 페이지를 만들면서 배우게 된 것들을 정리해 놓은 문서 입니다.
>
> 강의별 챕터에 따라 나뉘어 있습니다.

---

## 1. 시작하기

> ### 1.1 파비콘
>
> ```html
> <link rel="icon" href="./favicon.png">
> ```
>
> - 파비콘은 기본적으로 루트폴더에서 찾아서 적용하게 되어 있다. 하지만 해상도가 떨어져서 다른 파일을 이요하고 싶다면 위와 같이 적용시켜야 한다.
>
> 
>
> ### 1.2 오픈 그래프
>
> ![KakaoTalk Open Graph example](https://raw.githubusercontent.com/ParkYoungWoong/starbucks-vanilla-app/master/_assets/kakao_og_example.jpg)
>
> - 웹페이지가 **소셜 미디어(페이스북 등)**로 공유될 때 우선적으로 활용되는 정보를 지정
>
> > #### 1.2.1 오픈 그래프의 기본 정보
> >
> > - `og:type`: 페이지의 유형(E.g, `website`, `video.movie`)
> > - `og:site_name`: 속한 사이트의 이름
> > - `og:title`: 페이지의 이름(제목)
> > - `og:description`: 페이지의 간단한 설명 - **최대한 가결하게 작성**
> > - `og:image`: 페이지의 대표 이미지 주소(URL)
> > - `og:url`: 페이지 주소(URL)
>
>  
>
> ### 1.3 트위터 카드
>
> - 웹페이지가 **소셜 미디어(트위터)**로 공유될 때 우선적으로 활용되는 정보를 지정합니다.
>
> > #### 1.3.1 트위터 카드의 기본 정보
> >
> > - `twitter:card`: 페이지(카드)의 유형(E.g. `summary`, `player`)
> > - `twitter:site`: 속한 사이트의 이름
> > - `twitter:title`: 페이지의 이름(제목)
> > - `twitter:description`: 페이지의 간단한 설명
> > - `twitter:image`: 페이지의 대표 이미지 주소(URL)
> > - `twitter:url`: 페이지 주소(URL)
>
> **오픈 그래프와 트위터 카드 모두 작성해주는 것이 좋다**
>
>  
>
> ### 1.4 SEO
>
> - Search Engine Optimization
> - 검색 엔진에서 활용할 이미지
>
>  
>
> ### 1.5 Font
>
> - 용량이 크기 때문에 남발하지 않는 것이 좋다.
> - 서로 다른 브라우저에서도 서비스하기 위해 폰트를 지정
> - 라이센스 확인은 필수

---

## 2. Header & Dropdown menue

> - 도메인 주소는 생략이 가능하다
>
> ```html
> <a href="/">
> ```
>
> - 완전히 검은 글자색은 디자인적으로 촌스러울 수 있다.
> - "inner" 라는 ``division``을 만들어서 ``header``.``body`` 등과 같은 구역 내에 사용할 공간을 확보한다. inner에는 특별한 의미는 없다.
>
> ```css
> header .inner {
>   width: 1100px;
>   margin: 0 auto;
> }
> ```
>
> - ``inline``요소는 baseline 아래로 내려오는 경우를 대비해서 아래 쪽에 약간의 공간이 있다. ``inline``요소를 ``block``요소로 만들어 줆으로써 해결할 수 있다.
> - ``ul``태그와 ``li``태그는 단독으로 존재할 수 없다.
> - ``<a href="javascript:void(0)"></a>`` , ``#``은 해시라는 기능이 있기 때문에 ``void``를 더 권장
> - 자주 사용하는 클래스와 태그가 있기 때문에 하위 선택자를 명시할 땐 상위 선택자를 모두 명시해 주는 것이 좋다. (SCSS를 배우면 해결할 수 있다.)
>
> ```css
> header .sub-menu {}
> header .sub-menu ul.menu{}
> header .sub-menu ul.menu li{}
> header .sub-menu ul.menu li a{}
> ```
>
> - 중간중간에 일시적으로 특정 요소의 배경을 눈에 띄는 색으로 바꾸면 제작에 도움이 된다.
> - 요소 위치를 정할 때 ``flex``로만 하는 버릇이 있었는데, ``position``을 더 자주 사용했다. ``absolute``속성을 잘 사용하면 요소의 위치를 정하기가 훨씬 수월하다. 또한 불필요한 ``div``를 줄일 수 있다.
>
> 
>
> ### 2.1 position & margin 속성을 이용한 가운데 정렬
>
> ```css
>   height: 75px;				//정렬하고자 하는 요소의 높이를 지정해주어야 브라우저 계산할 수 있다.
>   position: absolute;
>   top: 0;					// 양 끝의 기준을 정해주어야 한다.
>   bottom: 0;				//
>   margin: auto;				//브라우저가 마진을 자동으로 계산
> ```
>
> 
>
> ### 2.2 메뉴의 클릭 영역 넓히기
>
> - 사용자 편의성을 위해서 필요한 부분
> - 글씨를 작게 만들어서 클릭하기 쉽도록 하기 위함
>
> ```css
> header .sub-menu ul.menu li a {
>   display: block;
>   font-size: 12px;
>   padding: 11px 16px;
>   color: #656565;
> }
> ```
>
> - ``inline``요소에 페이딩을 적용하기 위해서 ``block``요소로 만들어야 한다
>
> 
>
> ### 2.3 구분선 만들기
>
> ```css
> header .sub-menu ul.menu li {
>   position: relative;
> }
> 
> header .sub-menu ul.menu li::before {
>   content: "";
>   display: block;
>   width: 1px;
>   height: 12px;
>   background-color: black;
>   position: absolute;
>   top: 0;
>   bottom: 0;
>   margin: auto 0;
> }
> ```
>
> ![image-20210808060326599](note.assets/image-20210808060326599.png)
>
> - ``li``요소 중간중간에 구분선이 있는 게 아니라 ``absolute``를 이용해서 위에 띄워놓은 형태이다. 겹쳐져 있는 상태라고 볼 수 있다.
>
>  
>
> 