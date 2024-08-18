# 제너레이터/이터레이터

- 제너레이터: 이터레이터를 반환하는 함수
- 어떠한 값이든 이터러블이면 순회할 수 있습니다. 제너레이터는 이런 문장을 값으로 만들수 있고, 이 문장을 통해서 순회할 수 있는 값을 만들 수 있기 때문에 자바스크립트에서는 제너레이터를 통해서 어떠한 값이나 어떠한 상태든 순회하게 만들 수 있다.(중요)
```js
function *gen () {
  yield 1;
  yield 2;
  yield 3;
  return 100;
}

let iter = gen();

log(iter[Symbol. iterator]() == iter);
log(iter.next());
log(iter.next());
log(iter.next());
log(iter.next());

for (const a of gen()) log(a); // return값은 순회되지 않습니다
```