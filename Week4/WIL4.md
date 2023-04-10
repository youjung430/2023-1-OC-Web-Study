# GDSC 웹스터디 4주차
**HTML** : Hyper Text Markup Language   
**www** : World Wide Web   
## Tag
HTML 문서를 구성하는 기본 단위. `<tag>`형태로 태그를 열고, `</tag>`로 닫아주어야 한다.
```html
다양한 태그들
<h1>~</h6> 강조할때, 제목쓸때
<p> </p> 문단 나누기
<br> 줄바꿈
<strong> </strong>, <b> </b> 굵은 글씨
<mark> </mark> 형광펜
<u> </u> 밑줄
<input> 입력창
```
## Attribute
속성들은 요소에 대해 추가적인 정보를 제공한다. <태그 속성 = "값"> 의 형태로 사용되며, 태그마다 속성을 부여할 수 있고, 여러 속성을 부여할 수도 있다.    
예시 `<img src="images/200x200.png" alt="My image" width="100" height="200">`   
img 태그에서 src, alt, width, height 속성을 사용하고 있다.
## HTML 기본 구조
```html
<!DOCTYPE html>
<html>
    <head> 
        <meta    >
        <title> </title>
    </head>
    <body>
    </body>
</html>
```
`<!DOCTYPE html>` 도큐멘트 타입이 html임을 컴퓨터에게 알려준다.   
`<head>` head에는 대부분 화면에 나오지 않지만, 컴퓨터에게 주는 정보들이 적혀있다. 웹브라우저가 알아야 할 중요한 정보들이 들어간다.   
`<meta>` 문서의 키워드 또는 설정 등 문서와 관련된 여러가지 항목을 지정할때 사용하는데, 대표적으로 인코딩 방식을 설정해주는 charset이 있다.   
`<title>` 문서의 제목으로, 웹페이지의 탭에 표시된다.   
`<body>` 화면에 직접 출력되는 부분이다.