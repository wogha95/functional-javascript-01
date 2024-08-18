## 기존과 달라진 ES6에서의 리스트 순회

> for i++   
> for of

- 순회가 더 추상화됨

for of문은 키와 값으로 맵핑되어 순회되는 방식이 아니라는 것을 알 수 있음
`new Set([1, 2, 3])[1]` => undefined


### Array를 통해 알아보기

`Symbol.iterator은` 어떤 객체의 키로 사용될 수 있음
`arr [Symbol.iterator] = null` 를 실행하면 `for (const a of arr) log(a)` 에서 오류가 난다. 따라서 for...of 순회는 Symbol.iterator와 관련있음을 유추할 수 있다.


## 이터러블/이터레이터 프로토콜

자기 자신을 반환하는 Symbol.iterator 메서드를 가지고 있을때 well-formed 이터레이터/이터러블 이라고 합니다.
`log (iter2 [Symbol.iterator] () == iter2)`

어느 시점까지 진행된 이터레이터를 다시 진행할때 그때 그 상태를 유지할 수 있도록 자기자신을 바라보록 해야 well-formed가 된다.

그리고 ES6에서 지원하는 내장 값만 이 프로토콜을 따르는 것이 아니다.
이미 많은 오픈소스, 브라우저에서 순회가 가능한 값들은 대부분 이 프로토콜을 따르기 시작했다. 