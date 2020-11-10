> 참고: https://helloworldjavascript.net/ 를 바탕으로 정리하였습니다.

## 변수
__let__ 변수에는 값을 여러 번 다시 대입할 수 있지만, __const__ 변수에는 값을 한 번만 대입할 수 있고 선언 시에 값을 대입해주어야 함.(ES2015 도입)

* __let__ 보다 __const__ 를 사용하는것이 좋다. __let__ 을 사용하면 의도치 않게 다른 값이 대입되어 버리는 일이 생길 수 있기 때문. 정말로 재대입이 필요한 경우에만 __let__ 을 사용하는 것이 좋은 습관이다.
```
// let 변수 선언
let x = 1;

// 값 변경 가능
x = 2;

// const 변수 선언
const y = 1;

// 갑 변경 불가능
y = 2;  // 에러
```
---
## 타입

값의 종류. 자료형 이라고 부름. __typeof__ 연산자 활용.
```
typeof 1; // 'number'
typeof 'hello'; // 'string'
```
----
## number 타입
### __정수인지 실수인지 판별하기__
다른 많은 언어와는 다르게 Javascript는 정수와 실수를 별도의 타입으로 다루지 않음. 다만 어떤 수가 정수인지 실수인지는 판별가능 __Numer.isInteger()__ 메소드 사용.
```
Number.isInteger(1); // true
Number.isInteger(0.1); // false
```

### __number 타입의 특이한 값들__
- NaN(Not a Number) -> 계산 불가능한 연산의 결과값을 나타내기 위해 사용됨.
- -0
- Infinity
- -Infinity
```
0 / 0; // NaN
1 * 'hello'; // NaN

// NaN은 JavaScript의 값들 중 유일하게 자기 자신과 같지 않은 값이다. 따라서 어떤 값이 NaN인지 판별하기 위해서는 일반적인 비교 연산자를 사용하면 안 되고, 대신 Number.isNaN 또는 Object.is 함수를 사용해야 함.

const thisIsNan = NaN;

// 주의! 이렇게 하면 안 됩니다.
thisIsNan === NaN; // false

// 이렇게 해야 합니다.
Number.isNaN(thisIsNan); // true
Object.is(thisIsNan, NaN); // true
```


### __문자열을 number 타입으로__
```
parseInt('123'); // 123
parseInt('110', 2); // 6 (문자열을 2진수로 간주한다.)
parseFloat('12.345'); // 12.345
parseInt('hello'); // NaN
```

### __다른 타입과의 연산__
JavaScript는 number 타입과 다른 타입 간의 연산도 허용하지만, 그 결과가 별로 우아하지는 않음.
```
1 + null; // null
1 * '1'; // NaN
1 + '1'; // '11'
1 - '1'; // 0
```
위와 같이 피연산자의 타입, 연산자의 종류에 따라 결과값의 타입이 달라짐.
때문에 Javascript가 "일관적이지 않다"고 비난을 받음.
따라서 number 타입과 다른 타입의 연산은 웬만하면 피하는게 좋음.

특히 __prompt__ 나 __input__ 태그 등을 통해 입력받은 데이터는 __undefined__ 혹은 __문자열__ 일 가능성이 높음.
이 경우에는 __수 연산을 하기 전에__ 모든 __피연산자__ 를 확실히 __number 타입으로__ 만들어주는 것이 좋은 습관이라고 함.
```
const input = promp('정수를 입력하세요');
const num = parseInt(input);  // number 타입으로 만들어줌.
if(Number.isNaN(num)){
    alert('정수가 아닙니다');
}else{
    const result = num * 2;  // 안심하고 연산을 할 수 있음.
    alert(`${num}의 두 배는 ${result} 입니다.`);
}
```

### __Math 객체__
JavaScript에 내장된 Math 객체에는 수 연산을 위한 많은 메소드와 상수들이 내장되어 있음.
```
// 상수
Math.E // 자연상수 (2.71...)
Math.PI // 원주율 (3.14...)

// 삼각함수, 로그함수, 지수함수
Math.sin // 사인
Math.cos // 코사인
Math.tan // 탄젠트
Math.log // 밑을 자연상수로 하는 로그함수
Math.exp // 밑을 자연상수로 하는 지수함수
Math.sqrt // 제곱근

// 절대값, 올림, 내림, 반올림, 소수점 아래 잘라내기
Math.abs // 절댓값
Math.ceil // 올림
Math.floor // 내림
Math.round // 반올림
Math.trunc // 소수점 아래 잘라내기

// 최대값, 최소값
Math.max
Math.min

// 랜덤
Math.random
...
```
```
Math.cos(Math.PI); // -1
Math.log(Math.E); // 1
Math.round(0.5); // 1
Math.random(); // 0과 1 사이의 값이 임의로 반환됩니다.
Math.max(1, 2, 3, 4, 5); // 5
```

### __number 타입의 메소드__
number 타입은 객체가 아니지만, 마치 객체처럼 메소드를 사용할 수 있음. 이는 JavaScript가 래퍼 객체(wrapper object)라는 기능을 제공하기 때문.
```
(12345).toString(); // '12345'
(12345).toLocaleString(); // '12,345'
(1.2345).toFixed(2); // '1.23'
```