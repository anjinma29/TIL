## string타입

### 문자열 리터럴
Javascript는 문자열 값을 표현하기 위한 여러가지 리터럴을 제공.
```javascript
'hello'
"hello"
`hello`  // template literal
```

### 템플릿 리터럴
ES2015에서 도입. 문자열을 동적으로 생성하는 코드를 쉽게 작성할 수 있음/여러 줄로 이루어진 문자열 쉽게 표현 가능.
```javascript
const name1 = 'Foo';
const name2 = 'Bar';
const sentence = `${name1} meets ${name2}!`;
console.log(sentence);

// 일반적인 문자열 리터럴로는 아래와 같이 해야함.
name1 + ' meets ' + name2 + '!';
```
```javascript
`hello
world
hello
javascript!
`

// 일반적인 문자열 리터럴로는 아래와 같이 해야함.
'hello\nworld\nhello\njavascript!\n'
```
📎참고
'tagged template literal'. 주로 다은 언어를 Javascript와 통합할 떄 사용되고, 라이브러리 제작자가 아니라면 보통 tagged template literal을 위한 함수를 직접 제작할 일은 없음. [링크참조](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Template_literals#Tagged_template_literalshttps://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Template_literals#Tagged_template_literals)
```javascript
styled.div`display: flex; border: 1px solid black;`; // styled-components
gql`query { user { name }}`; // graphql-tag
html`<title>Hello tagged template literal!</title>`; // lit-html
```