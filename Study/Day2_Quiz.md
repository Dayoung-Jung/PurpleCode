# Quiz
1. 호출할 때 마다 1씩 증가된 점수를 반환하는 함수를 만들어보세요
2. 전역변수 ㅇㅣ용
3. 클로저 사용
4. 클로저를 사용하되 화살표 함수로 구현
5. 함수 속성(동적 바인딩) 사용
---
- 내가 만든 코드 
```javascript
const makeSum = () => {
    let score = 0;

    return () => ++score;
};

let score = makeSum();

console.log(score);
console.log(score);
console.log(score);
```  

- 다른 사람들 중 우수 코드
```javascript
let num = 0;
function count(num) {
  return ++num;
}
const count2 = (function(){
  let num1 = 0;
  return function(){return ++num1};
}())
console.log(count2());
const count2 = (function(){
  let num2 = 0;
  return () => ++num2
}())
```