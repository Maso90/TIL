# Lexical(Static) scope
함수를 어디서 호출하는지가 아니라 어디에 선언하였는지에 따라 결정된다.
```javascript
var x = 1;
function foo() {
    var x = 10;
    bar();
}
  
function bar() {
    console.log(x);
}
foo(); // ?
bar(); // ?
```
자바스크립트는 렉시컬 스코프를 따르므로 함수를 선언한 시점에 상위 스코프가 결정된다.   
함수를 어디에서 호출하였는지는 스코프 결정에 아무런 의미를 주지 않는다.   
위 예제의 함수 bar는 전역에 선언되었다.   
따라서, 함수 bar의 상위 스코프는 전역 스코프이고 위 예제는 전역 변수 x의 값 1을 두번 출력한다.

[모던 자바스크립트-scope](https://poiemaweb.com/js-scope)