# JavaScript_Study01
- 스터디 일자: 2020/10/17
- 스터디 내용
    - webstorm 플러그인 설치
    - javascript 코드 구조
    - javascript 변수
    - javascript 형변환
    - javascript 연산자
    - javascript 조건문 
---
### console
```javascript
console.log("첫 세미나 입니다.");
console.log("첫번째 문");
console.log("두번째 문");
console.info("정보");
console.warn("경고");
console.error("에러");
```

### alert
- alert: 경고 메세지
```javascript
alert("안녕하세요.");
```

### 주석
- 한줄 주석
```
// 한줄 주석
```
- 여러줄 주석
```
/*
* 여러줄 주석
*
* 
*/
```

### 변수 설정
- `var` (요즘 잘 안씀)
```javascript
var foo = 10;
console.log(foo);

var foo = 10, bar = 10;
console.log(foo, bar);
```
- `let` : `var`의 단점을 극복한 키워드
```javascript
let a = 10, a= 20;
console.log(a);
```
- `const` : `let`과 다르게 변하지 않는 값을 선언 할 때 사용
```javascript
const result = 1;
console.log(result);
```

### `var` 가 아닌 `let`, `const` 를 쓰는 이유
##### 1. 중복된 변수 이름이 에러가 나지 않아 불편함
```javascript
var name = "정다영"
console.log(name);

var name = "정다영"
console.log(name);
```

##### 2. 지연 변수가 전역 변수처럼 밖에서도 사용이 됨
```javascript
var name = "정다영"

if (name === "정다영") {
    var success = true;
} else {
    var success = false;
}

console.log(result);
```
##### 3. run 하면 var로 선언한 변수가 맨 위로 올라와서 실행 됨
- 면접에서 호이스팅에 대한 질문이 많이 나옴
```javascript
console.log(a);
var a = 10;
```

### null VS undefined
- null: 값이 없는 것
```javascript
const a = null;
```
- undefined: 값을 할당해주지 않았다.
```javascript
const b;
```

### 변수 이름 정하는 규칙
- 자바스크립트에서는 카멜 케이스를 잘 씀
```javascript
const purpleCode = 10;
```
- 고유값은 대문자로 하는게 좋음
```javascript
const BLACK = "#000000"
```

### 자바스크립트 변수
- 크게 원시 타입이랑 객체 타입이 있다.

### 문자열 표현
```javascript
const name = "정다영"
console.log("안녕하세요 저는" + name + "입니다." );
console.log(`안녕하세요 저는 ${name}입니다.`);
```

### 자료형 변환
- 문자형으로 변환
    - alert: 자료형 변환해준다
```javascript
let foo = 1000;
console.log(typeof foo); // number

foo = string(foo);
console.log(typeof foo); // string
```
- 숫자형으로 변환
```javascript
let str = "12345";
let num = Number(str);
console.log(typeof num); // number
```
```javascript
console.log("6"/"3");
console.log("6" + "3"); // 이건 안됨.
```

- 불린형으로 변환
```javascript
console.log(Boolean(value : 1));
console.log(Boolean(value : 0));
```





### 산술 연산자
```javascript
let number =10;
number++; // 다음줄에서 더해진다.
++number; // 그 줄에서 더해진다.

number += 20;
number = number + 20;

number -= 20;
number = number - 20;
```

### 논리 연산자
-  `!`: not
-  `&&` : and
-  `||` : OR
```javascript
console.log(!!true);
```

### 비교 연산자
- `==` : 타입 검사 안하고 같은지만 판단
- `===` : 타입 검사까지 하면서 같은지 판단
```javascript
const a = 10;
const b = "10";

console.log(a == b); // true
```
```javascript
// 이름 출력 함수_1
const interoduce = name => {
    if ( !name ){
        console.log("이름이 정의되지 않았습니다.");
        return;
    }
    console.log(`나의 이름은 ${name} 입니다.`);
}
```
```javascript
// 이름 출력 함수_2
const interoduce = name => {
    if (name === undefined){
        console.log("이름이 정의되지 않았습니다.");
        return;
    }
    console.log(`나의 이름은 ${name} 입니다.`);
}
```
```javascript
console.log(true || false); // true

const name = "정다영";
console.log(name || "없음"); // 정다영
console.log(name && "있음"); // 있음
console.log(undefined && "없음"); // undefined
```


### 삼항 연산자
##### 조건 ? 참 일 경우 : 거짓 일 경우
- 긴 코드는 if 문 , 짧은 테스트 느낌은 삼항 연산자 쓰는게 좋음

```javascript
const name = "정다영";
if(name === "정다영") {
    console.log("HI");
} else {
    console.log("BYE");
}
```
```javascript
name === "이성종" ? console.log("HI") : console.log("BYE")
```

### null 병합 연산자
- `??`: null과 undefined 인지를 체크 함 / 정의된 값을 반환
- `||` 첫번째 truthy 값을 반환
```javascript
const a = null;
const b = 10;

a !== null && a !== undefined ? a : b ;
```
```javascript
let width = 0;

width = width || 1000;
width = width ?? 1000;
```

### 조건문
##### 연습 코드
```javascript
const number = 10;

if (number === 10) {
    console.log(number);
}
```