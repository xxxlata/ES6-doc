# ES6 기초

## 1.Dead Zone 

let의 temmporal dead zone? 

ex)let 도입 이전의 코드 

```
var myName = 'juha';
console.log(myName);

결과값 = juha

console.log(myName);
var myName = 'juha';  
결과값 = undefined

```
//자바스크립트의 문법 상 variable 선언은 프로그램 동작 순서에 따라 위에서 시작되는 것 이 맞다.
//그러나 이러한 에러를 잡아내지 못 함. hoisting 하기 때문이다.

*hoisting = 자바스크립트가 프로그램을 작동시키기 전 var값을 위로 옮겨주는 동작.

ex) let 도입 후의 "오작동" 코드

```
console.log(myName);
let myName = 'juha';    <- let의 temporal <dead zone> 

결과값 = error
```
## 2.Block Scope

{} 괄호로 이루어진 block scope

```
let hello = hello;  <- 외부의 값
const bye = bye;

function a (){
    console.log(hello);  <- 내부의 값
}
```
let 과 const 는 모두 block scope로 되어있다.
이는 외부에서 (블록)내부로 값을 끌어올 수 있지만 내부에서 외부로 값을 끌어올 수 없다는 것을 의미한다. 

## arrow functions

arrow function이란 코드를 보다 쉽게 볼 수 있게 만든  방법. (=>)

ex) 기존 function 방식

```
const names =['tomato', 'potato','banana'];

const dotted = names.map(function(item)
return item + ".";
);

console.log(dotted);
```
*map? 각각의 아이템마다 함수를 호출해준다. return (itme)이 반드시 필요하다.

ex) arrow function 방식 

```
const names =['tomato', 'potato','banana'];

const dotted = names.map(item => item + ".");

console.log(dotted);
```

핵심은 implicit return 을 이용한 점이다. 

*implicit return = "같은 줄"에 어떤 것을 적던지 return 시켜주는 방식.

++ 추가 설명

(아이템 값이 두 개인 경우)

```
const names =['tomato', 'potato','banana'];

const dotted = names.map((item,index) => item + "." + index); // index는 숫자를 붙여준다.

console.log(dotted);
```

(아이템 값이 없는 경우)

```
const names =['tomato', 'potato','banana'];

const dotted = names.map(() => "."); // 결과값은 점만 찍힌 리스트 값이 출력

console.log(dotted);
```