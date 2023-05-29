# GDSC 웹스터디 9주차
## 브라우저 동작 원리
자바스크립트는 브라우저에서 HTML, CSS와 함께 실행됨. -> 브라우저 환경 고려 필요   
브라우저의 핵심 기능은 웹페이지를 서버에 요청하고, 받은 응답을 브라우저에 표시하는 것. HTML, CSS 파일은 렌더링 엔진의 HTML파서와 CSS파서에 의해 파싱되어 DOM, CSSOM 트리로 변환, 렌더 트리로 결합됨. 이를 기반으로 웹페이지 표시됨.
</br>  
* **DOM**이란?   
웹페이지의 콘텐츠 및 구조, 스타일 요소를 구조화 시켜 프로그래밍 언어가 해당 문서를 읽고 조작할 수 있도록 API제공.
![image1](https://t1.daumcdn.net/cfile/tistory/993F223B5A73F9C406)
</br>

HTML에서 Javascript 쓰는 위치 (CSS와 유사)   
1. script 태그 안에 작성.
2. 외부 자바 스크립트 코드 가져오기. (이때도 script 태그 사용)   


브라우저는 **동기**적으로 HTML, CSS, Javascript을 처리함. script 태그의 위치에 따라 블로킹이 발생하여 DOM의 생성이 지연될수도 있음. -> body 요소의 가장 아래에 자바스크립트를 위치시키자
1. HTML 요소들이 스크립트 로딩 지연으로 인해 렌더링에 지장 받는 일이 발생하지 않아 페이지 로딩 시간 단축.
2. DOM이 완성되지 않은 상태에서 자바스크립트가 DOM을 조작하면 에러 발생 가능.
</br>

## 객체
자바스크립트 : 객체 기반의 스크립트 언어   
### 프로퍼티
데이터를 의미. 키 + 값으로 구성됨.
* 프로퍼티 키 : 빈 문자열을 포함하는 모든 문자열 또는 symbol 값. 프로퍼티를 식별하기 위한 식별자
* 프로퍼티 값 : 모든 값
### 메소드
프로퍼티 값이 함수일 경우 일반 함수와 구분하기 위해 메소드라고 부름.
```javascript
var emptyObject = {}; // 중괄호를 사용하여 객체 생성
var person = {
    name: 'LEE',
    gender: 'male';
}; // {}내에 프로퍼티 기술

var person = new Object(); // 빈 객체
person.name = 'Lee'; // 프로퍼티 추가

function Person(name, gender){
    this.name = name;
    this.gender = gender;
}; // 생성자 함수
var person1 = new Person('Lee', 'male');
var person2 = new Person('Kim', 'female'); // 인스턴스 생성

var person = {
    'first-name': 'Ung-mo'
}; // 프로퍼티 키
console.log(person['first-name']); // 프로퍼티 값 읽기
person['first-name'] = 'kim'; // 값 갱신
```
</br>

## 함수
1. 동일한 작업 반복 수행할때 효율적
2. 코드 재사용 가능
3. 코드 길이 줄어듦

### 정의 방식
1. 함수 선언문
```javascript
function square(number) {
    return number*number;
}
```
2. 함수 표현식
```javascript
var square = function(number){
    return number*number;
}
var bar = square; // square, bar 동일한 익명 함수의 참조값을 가짐
```

### 함수 호이스팅
```javascript
var res = square(5); // 오류 발생

var squrae = function(number){
    return number*number;
} 
```
함수 선언문과 달리 함수 표현식의 경우 함수 호이스팅이 아니라 변수 호이스팅이 발생함. runtime에 해석, 실행됨.   
### call-by-value vs call-by-reference
![image2](https://poiemaweb.com/img/call-by-val&ref.png)

### 함수 객체의 프로퍼티
함수는 객체이므로 프로퍼티를 가질 수 있음
* arguments : 매개변수 갯수가 확정되지 않은 가변 인자 함수를 구현할 때. 유사 배열 객체.
* caller : 자신이 호출한 함수를 의미.
* length : 함수 정의시 작성된 매개변수 갯수.
* name : 함수명.
</br>

## 배열
1개의 변수에 여러개의 값을 순차적으로 저장할 때.
### 생성
```javascript
const arr = ['zero', 'one', 'two']; // 배열 리터럴. 요소 접근 위해 인덱스 사용.
const obj = {'0':'zero', '1':'one', '2':'two'}; // 객체 리터럴로 유사하게 표현. 프로퍼티 명을 키로 사용.

const arr = new Array(1,2,3); // Array() 생성자 함수 사용
```
</br>

## 이벤트
사용자가 브라우저에 일으킨 사건.   
브라우저에 a라는 사건이 발생 -> b라는 일을 수행.
* 마우스 사용 이벤트   
    : click, dbclick, mousedown...
* 키보드 사용 이벤트   
    : keydown, keyup, keypress...