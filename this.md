# this의 간단한 rule

1. 함수를 호출할 때 new 키워드를 사용하면 함수 내부의 this는 완전히 새로운 객체입니다.
    ```javascript
    function ConstructorExample() {
        console.log(this);
        this.value = 10;
        console.log(this);
    }new ConstructorExample();
    // -> {}
    // -> { value: 10 }
    ```
2. 함수를 호출/생성하기 위해 apply, call 또는 bind를 사용하는 경우 함수 내부의 this가 인수(arguments)로 전달되는 객체입니다.
    ```javascript
    function fn() {
        console.log(this);
    }
    var obj = {
        value: 5
    };
    var boundFn = fn.bind(obj);boundFn(); // -> { value: 5 }
    fn.call(obj);  // -> { value: 5 }
    fn.apply(obj); // -> { value: 5 }
    ```
3. obj.method()—this 와 같이 함수가 메서드로 호출되는 경우 함수가 속성인 개체입니다.
    ```javascript
    var obj = {
        value: 5,
        printThis: function() {
            console.log(this);
        }
    };
    obj.printThis(); // -> { value: 5, printThis: ƒ }
    ```
4. 함수가 자유 함수 호출로 호출되는 경우(위에 제시된 조건 없이 호출됨을 의미) 이것이 전역 개체입니다. 브라우저에서는 window 객체입니다. 엄격 모드('use strict')인 경우 전역 객체 대신 정의되지 않습니다.
    ```javascript
    function fn() {
        console.log(this);
    }// If called in browser:
    fn(); // -> Window {stop: ƒ, open: ƒ, alert: ƒ, ...}
    ```
5. 위의 규칙이 여러 개 적용되는 경우 더 높은 규칙이 이기고 이 값을 설정합니다.
6. 함수가 ES2015 화살표 함수인 경우 위의 모든 규칙을 무시하고 생성 시 주변 scope의 this 값을 받습니다.
    ```javascript
    const obj = {
        value: 'abc',
        createArrowFn: function() {
            return () => console.log(this);
        }
    };
    const arrowFn = obj.createArrowFn();
    arrowFn(); // -> { value: 'abc', createArrowFn: ƒ } 
    ```

`Reference`
---
[The Simple Rules to ‘this’ in Javascript](https://codeburst.io/the-simple-rules-to-this-in-javascript-35d97f31bde3 "The Simple Rules to ‘this’ in Javascript")

[javascript this의 4가지 동작 방식](https://yuddomack.tistory.com/entry/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-this%EC%9D%98-4%EA%B0%80%EC%A7%80-%EB%8F%99%EC%9E%91-%EB%B0%A9%EC%8B%9D)