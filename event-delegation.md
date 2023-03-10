# 이벤트 위임이란?
> 핵심은 이벤트 동작시 event.target으로 이벤트를 핸들링 하는 것입니다.

* 이벤트 리스너를 하위 요소에 추가하는 대신 상위 요소에 추가하는 기법
* 리스너는 DOM의 event bubbling으로  인해 하위 요소에서 이벤트가 발생될 때마다 실행
* 장점
    * 하위 요소에 이벤트 핸들러 연결 없이 상위 요소에 단일 핸들러만 존재하기 때문에 메모리 사용 공간 절약
    * 제거한 요소에서 핸들러를 제거하고 새 요소에 바인딩 할 필요가 없음
* 단점
    * 이벤트 위임한 부분의 내부에서 이벤트 동작이 일어날 경우 코드로 추가 처리가 필요합니다.

```javascript
document.getElementById("myDiv").addEventListener("click",function(e) {
	// e.target was the clicked element
  if (e.target && e.target.matches("a.classA")) {
    console.log("Anchor element clicked!");
	}
});
```
[Javascirpt.info - 이벤트 위임](https://ko.javascript.info/event-delegation)