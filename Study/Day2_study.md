# Javascript_Study02
- 스터디 일자: 2020/10/24
- 스터디 내용
    - javascript 함수 기본
    - javascript 반복문
    - javascript 객체
---
### **함수 선언**
- 함수란?

특정 코드를 하나의 명령으로 실행할 수 있게 해주는 것
```javascript
const name = "정다영";
const home = "mapogu";

const name2 = "홍길동";
const home2 = "seoul";

console.log(`이름은 ${name}이며 집은 ${home}입니다.`);
console.log(`이름은 ${name2}이며 집은 ${home2}입니다.`);
```  

- 함수 선언
    - 이름, 집주소 출력하는 함수 만들기
    ```javascript
    function introduce(name, home) {
        console.log(`이름은 ${name}이며 집은 ${home}입니다.`);
    
    }
    
    introduce("정다영","mapogu");
    introduce("홍길동", "seoul");
    ```  
  
    - sum 함수 만들기
    ```javascript
    function add(a, b) {
        return a+b;
        // 이 밑에 뭐 쓰면 실행 안됨
        // 리턴 후에는 그냥 함수가 끝나는 것
    }
    
    console.log(add(1,3));
    console.log(add(4,5));
    ```  
    
    - undefined 함수 출력
    ```javascript
    function reFunc() {
          return;
      }
      
      console.log(reFunc()); // undefined 출력
    ```  
  
- 잘못된 함수와 보완된 함수
    - 잘못된 함수
    ```javascript
    function introduce (name, home) {
        console.log(`이름은 ${name}이며 집은 ${home}입니다.`);
    }
    
    introduce("null","mapogu");
    ```  
    
    - 수정한 함수
    ```javascript
    function introduce (name, home) {
        if (!name || !home){
            console.log("정확한 값이 입력되지 않았습니다.");
            return;
        }
        if (typeof name !== "string" || typeof home !== "string") {
            console.log("정확한 값이 입력되지 않았습니다.");
            return;
        }
        console.log(`이름은 ${name}이며 집은 ${home}입니다.`);
    }
    
    introduce("정다영","mapogu");
    introduce("홍길동","seoul");
    ```  
  
- 인수의 기본값
    - Nan 값 출력
    ```javascript
      function add(a,b) {
          return a+b;
      }
  
      console.log(add(1,)) // NaN             
    ```  
  
    - 기본값 할당 (1)
    ```javascript
    function add(a,b=0) {
        return a+b;
    }
    
    console.log(add(1,)) // NaN
    ```  
  
    - 기본값 할당 (2)
    ```javascript
    function add(a,b) {
        if(!a){
            a=10;
        }
        if (!b){
            b=10;
        }
        return a+b;
    }
    
    console.log(add(1,)) // NaN
    ```  
  
- 함수 표현식과 함수 선언문
    - 함수 선언문
        함수는 주요 코드 흐름 중간에 독자적인 구문 형태로 존재한다.
        ```javascript
        function sum(a,b) {
            return a+b;
        }
        ```
        ```javascript
        'use strict'
        
        const name = "이재준";
        
        if (name) {
          function introduce() {
            console.log(`안녕하세요 ${name}입니다.`);
          }
        } else {
          function introduce() {
            console.log("이름이 정의되지 않았습니다.");
          }
        }
        
        introduce(); // error! : introduce is not defined
        ```  
     - 함수 표현식
        함수는 표현식이나 구문 구성 내부에 생성된다.
        함수가 할당 연산자 `=`이용해 만든 `할당 표현식` 우측에 생성된다.
        ```javascript
        let sum = function (a, b){
            return a + b ;
        }
        
        console.log(sum(1,2));
        ```   
        ```javascript
        const name = "이재준";
        
        const introdcue = name
          ? function() {
              console.log(`안녕하세요 ${name}입니다.`);
            }
          : function() {
              console.log("이름이 정의되지 않았습니다.");
            };
        
        introdcue(); // 정상적으로 호출
        ```  
- 가변 인수
    - 두개의 값을 받을 경우
    ```javascript
    function add(a, b) {
        return a+b ;
    }
    
    console.log(add(1, 3))
    ```  
    - 세 개 이상의 값을 받을 경우
    ```javascript
    function add() {
        lst sum = 0;
    
        console.log(arguments)
    
        for (let i=0; i<arguments.length; i++){
    
            sum += arguments[i];
        }
        return sum;
    }
    ```  
    ```javascript
    function add(a, b, ... g) {
        let sum =0;
    
        for (let i=0; i<arguments.length; i++) {
    
            sum += arguments[i];
        }
    
            return a*b+sum;
    }
    
    console.log(add(1,2, 3,4,5,6,6,7,7));
    ```  
- 일급함수
    프로그래밍 언어에서 함수를 값처럼 다루는 것을 일급함수하고 한다.
    ```javascript
    let add = function add(a, b) {
      return a + b;
    };
    
    let result = add(1, 2);
    
    console.log(result);
    ```  
- 고차 함수
    함수를 결과로 반환하거나, 함수를 인자로 전달 받는 함수
    ```javascript
    // 함수를 return 하는 함수
    function person(name) {
      function introduce() {
        return "안녕하세요. 제 이름은 " + name + "입니다.";
      }
    
      return introduce;
    }
    
    const jaejun = person("이재준");
    const naerim = person("김내림");
    
    console.log(jaejun());
    console.log(naerim());
    
    // 함수를 인자로 받아 대신 실행하는 함수
    function callWith10(val, func) {
      return func(10, val);
    }
    
    function add(a, b) {
      return a + b;
    }
    
    callWith10(20, add);
    ```  
  
- 콜백 함수
    함수를 인자로 다른 함수에 넘겨주고 해당 함수 안에서 인자로 받은 함수를 호출하는 것을 콜백함수라고 한다.
    ```javascript
    function callbackExample(a, b, f) {
      setTimeout(() => {
        f(a + b);
      }, 5000);
    }
    
    callbackExample(10, 20, function(result) {
      console.log(`sum : ${result}`);
    });
    ```  
  
- 화살표 함수
    ```javascript
    function add (a,b) {
        return a+b;
    }
    
    const add = (a,b) => a+b;
    
    console.log(add(1,3));
    ```  
  
- 즉시 실행 함수 (절대 안쓰는 함수)
    ```javascript
    (function() {
        console.log("aa");
    }); ()
    ```  
  
- 클로저
    함수 안에 있는 특정한 값이나 변수를 기억하는 것이 클로저
    ```javascript
    const makeCounter = () => {
        let count = 0;
    
        return () => ++count;
    };
    
    let count = makeCounter();
    
    console.log(count);
    console.log(count);
    console.log(count);
    ```
- 함수 이름 짓기
    - get... -> 어떤한 값을 반환하는 함수
    ```javascript
    const getName = () => {
        return name;
    }
    ```
    - calc... -> 어떠한 값을 계산하는 함수 
    ```javascript
    const calcValue = () => {
        return result;
    }
    ```
    - create... -> 어더한 값을 생성하는 함수
    ```javascript
    const createName = () => {
        return result;
    }
    ```
    - check... -> 어떠한 값을 확인하는 함수
    - fetch... -> 어떠한 데이터를 외부에서 가져오는 함수
    
- 함수 생성시 주의사항
    1. 함수를 간결하게 만들면 테스트와 디버깅이 쉽다.
    2. 코드를 자기 설명적 코드로 만들어 어떠한 동작을 하는지 알기 편한다.
    3. 이렇게 함수를 활용할 경우 코드가 정돈되며 가독성이 높다.  
 
---    
### **반복문**

- for 문
    ```javascript
    let sum = 0;

    for (let i = 1; i <= 10; i++) {
      sum += i;
    }

    console.log(sum);
    ```   
- for...in 문
    ```javascript
    const me = {
        name: "이재준"
        home: "mapogu"
    };
    
    for(let key in me) {
        console.log(// 못쑵 싀발);
    
    }
    ```  

- for...of 문
    ```javascript
    let sum = 0;
    let numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
    
    for (let number of numbers) {
      sum += number;
    }
    
    console.log(sum);
    ```

- while 문
    ```javascript
    let sum = 0;
    let i = 1;
    
    while (i <= 10) {
      sum += i;
      i++;
    }
    
    console.log(sum);
    ```  
    
- do while 문
    ```javascript
    let sum = 0;
    let i = 1;
    
    do {
      sum += i;
      i++;
    } while (i <= 10);
    
    console.log(sum);
    ```  
  
- break 와 continue
    ```javascript
    let sum = 0;
    
    for (let i = 1; i <= 20; i++) {
      if (i % 2 !== 0) continue;
      sum += i;
      if (i === 10) break;
    }
    ```  
---
### **객체**

- 객체
    - 웝시 타입: 1, 1.1, "ㄴㄴㄴ"
    - 객체 타입: 배열  
    

- 객체를 만들어 주는 법
    1. 객체 리터럴
    ```javascript
    const me = {
      name: "정다영",
      age: 21,
      home: "mapogu"
    };
    ```  
    2. 함수를 사용한 객체 생성
    ```javascript
    const createPeople = (name, age, home) => ({ name, age, home });
    
    const me = createPeople("정다영", 21, "mapogu");
    ```  
    3. new 연산자 사용
    ```javascript
    function People(name, age, home) {
      this.name = name;
      this.age = age;
      this.home = home;
    }
    
    const me = new People("정다영", 21, "mapogu"); 
    ```  
    4. Object()
    ```javascript
    const me = new Object(); // 기본 객체 생성
    
    me.name = "정다영";
    me.age = 21;
    me.home = "mapogu";
    ```  
 - 객체 동적 바인딩 (생성, 수정, 삭제)
 ```javascript
const me = {
    name: "정다영",
    home: "mapo"
};

me.name = "홀길동" // 생성
me.hobby = "baseball" // 생성
delete me.hobby; // 삭제
```  

- 해당 프로퍼티가 존재하는지 확인하기
```javascript
const makeStudent = (name,home) => ({name, home, crew: "purple code"});

const me = makeStudent(name: "정다영", home: "mapo");
const you = makeStudent(name: "김내림", home: "aaa");

console.log(me);
console.log(you);

console.log("name" in me); // 안에 값이 있는지 없는 지 확인하는 거

```  

- 정수 프로퍼티를 활용한 객체 정렬
```javascript
const students = {
  "1": "이재준",
  "3": "이성현",
  "2": "김내림",
  "5": "송현주",
  "4": "정지만"
};

for (let student in students) {
  console.log(student); // 1 2 3 4 5
  console.log(students[student]);
}
```  

- 비구조화 할당
```javascript
const introduce = ({ name, age }) => {
  // const {name, age} = ooo;
  console.log(`안녕하세요 저는 ${name}입니다. 저의 나이는 ${age}살 입니다.`);
};

const jjl = {
  name: "이재준",
  age: 23,
  hobby: "music"
};

introduce(jjl);
```  

- spread
```javascript
const purpleCode = {
  crew: "purple Code"
};

const purpleCodeStudent = {
    ...purpleCode, // purpleCode 에 있는거 펼쳐준다
    name: "이재준"
};
```  

- rest
```javascript
const me = {
    name: "정다영",
    home: "mapo",
    xxx: 123
};

const {name, ... rest } = me;
console.log(name, rest);
```  
- 객체의 복사
    - 원시 복사
    ```javascript
    let name = "정다영" ;
    let newName = name;
    ```  
    - 객체 복사
    ```javascript
    const me = {
        name: "이재준",
        home: "mapo"
    };
    
    const admin = me;
    
    admin.name = "김내림";
    ```  
- 메서드와 this
    - 일반 메서드
    ```javascript
    const me1 = {
      name: "이재준",
      age: 23,
      introduce: function() {
        console.log("안녕하세요!");
      }
    };
    ```  
    - 축약형 메서드
    ```javascript
    const me2 = {
      name: "이재준",
      age: 23,
      introduce() {
        console.log("안녕하세요!");
      }
    };
    ```  
    - 화살표 함수로 만들어본 메서드
    ```javascript
    const me3 = {
      name: "이재준",
      age: 23,
      introduce: () => console.log("안녕하세요!")
    };
    
    me1.introduce(); // 안녕하세요!
    me2.introduce(); // 안녕하세요!
    me3.introduce(); // 안녕하세요!
    ```  
    - this
    ```javascript
    const me = {
      name: "이재준"
    };
    
    const naerim = {
      name: "김내림"
    };
    
    function introduce() {
      console.log(`안녕하세요 저는 ${this.name}입니다.`);
    }
    
    me.introduce = introduce;
    naerim.introduce = introduce;
    
    me.introduce();
    naerim.introduce();
    ```  
  