# 함수

반복적으로 필요한 코드를 하나의 덩어리로 묶어서 필요할 때마다 꺼내 쓸 수 있도록 한것이죠!

```jsx
function 나의시크릿라면레시피(){
	let 라면그릇;
	
	물 550ml를 끓인다;
	면과 분말 스프, 후레이크를 같이 넣는다;
	4분 40초간 더 끓인다;

	라면그릇 = 맛있는라면;

	return 라면그릇;
}

나의시크릿라면레시피();
```

## 3.1 함수 구조

함수는 기본적으로 아래의 형태를 가집니다.

```jsx
function 함수이름(parameter1, parameter2...) { // 함수의 선언
    // 실행코드...
    return 반환값
}

함수이름(argument1, argument2...) // 함수의 호출
```

이를 그림으로 표현하자면 아래와 같은 형태일 것입니다.
![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/e8f11927-b70c-4524-9227-a3efac08e7aa/2acd2560-59ef-4d11-9e6e-e79ef65b2eef/Untitled.png)

## 3.2 함수의 활용 - 매개변수와 전달인자.

| 용어 | 번역 | 의미 |
| --- | --- | --- |
| Parameter | 매개변수 | 함수와 메서드에 입력 변수 이름 |
| Argument | 전달인자, 인자, 인수 | 함수와 메서드에 실제 입력되는 값 |

파라미터(매개변수)와 아규먼트(전달인자)는 용어를 구분해야 합니다. 쉽게 **파선아실(파라미터는 선언, 아규먼트는 실제 값)**이라고 줄여 부르기도 합니다.

여기서 console.log와 return은 구분할 필요가 있습니다. console.log는 콘솔 창에 표시되는 단순 출력이며, return은 해당 함수가 실행되면 반환되는 값을 전달합니다. 또한 함수 내부에서 return 구문을 만나게 되면 해당 함수는 **종료**됩니다.

아래 1번, 2번, 3번, 4번 출력 결과를 각각 비교해보세요.

```jsx
// 함수
// 읽어볼만한 문헌 : https://ko.javascript.info/function-basics

// 1번
function 안녕(파라미터){
    console.log(파라미터);
    console.log('hello');
    return 100;
}

let 아규먼트 = 1000;
안녕(아규먼트);
console.log(안녕(아규먼트) + 안녕(아규먼트));

// 2번
function 안녕(){
    console.log('hello');
}

안녕();
console.log(String(안녕()) + String(안녕()));

// 3번
function 안녕(){
    console.log('hello')
    return 10
}

안녕()
console.log(String(안녕()) + String(안녕()))

// 4번
function 안녕(){
    console.log('hello')
    console.log('hello')
    console.log('hello')
    return
    console.log('hello')
    console.log('hello')
    console.log('hello')
}

안녕()
```
함수는 아래와 같은 이유로 사용합니다.

1. 재사용성이 높아집니다.
2. 유지보수가 용이합니다.
3. 구조 파악이 용이합니다.
    
    ```jsx
    땅파기() // 10만줄
    기반다지기() // 10만줄
    기둥세우기() // 10만줄
    벽돌쌓기() // 10만줄
    지붕올리기() // 10만줄
    ```
    

### 3.2.1 함수의 활용 - 함수의 아규먼트에 따른 반환값

함수에 전달되는 아규먼트 즉 **인자**는 매개변수보다 적거나 많아도 에러가 발생하지 않습니다.

```jsx
function 함수1 (a, b, c){
    return a + b + c
}

// 콘솔창의 기능이에요. 마지막 라인에 한하여 console.log()를 찍지 않아도 return값을 console창에 출력해줍니다.
함수1(10, 20, 30) 
함수1(10, 20, 50)

// 다음 실행 값은?
console.log(함수1(10, 20, 30))
console.log(함수1(10, 20, 50))

// 필요 이상의 아규먼트를 넣었을 때
함수1(10, 20, 30, 40) // Error를 뿜지 않습니다. 60

// 필요 이하의 아규먼트를 넣었을 때
함수1(10, 20)

/*
function 함수1 (a, b, c){
    return a + b + String(c)
}
함수1(10, 20) // '30undefined'
*/
```

## 3.3 함수를 선언하는 여러가지 방법

1. 함수 선언문과 함수 표현식

함수는 function + 제목 + ( ) + { } 의 조합인 구문(Statement)으로 선언할 수도 있고, 제목 없이 선언하여 값으로 할당하는 표현식(Expression)으로 선언하는것도 가능합니다.

```jsx
// 함수 선언문
function sum(x, y){
  return x + y;
}

// 함수 표현식
let sumXY = function(x, y){
  return x + y;
};
console.log(sum(10, 20));
console.log(sumXY(10, 20));
```

<aside>
💡 **구문(Statement)과 표현식(Expression)**
**구문**은 자바스크립트 명령문으로, 어떤 작업을 수행하기 위한 코드 블록이라 할 수 있습니다. 예를 들어 우리가 뒤에서 배울 if문, switch문, for문 등이 여기에 포함됩니다.
**표현식**은 값으로 평가될 수 있는것을 의미합니다. 숫자나 문자열 같은 값 자체나 5 < 3 와 같은 비교 연산자등이 여기에 해당합니다. 위에서 함수표현식이라 함은 함수를 값 처럼 사용하기 때문에 그렇게 표현합니다.

</aside>

1. 화살표함수

함수는 선언 시 function 키워드를 화살표 기호로 대체하여 표현할 수 있습니다. 화살표 함수는 선언 시 제목을 정할 수 없기 때문에 표현식으로 사용해야 합니다.

```jsx
// 읽어볼만한 문헌 : https://ko.javascript.info/arrow-functions-basics

function 함수1(x, y) {
    return x + y
}
// 위 함수를 화살표 함수로 작성하면 아래와 같습니다.
let 함수1 = (x, y) => x + y

// 만악 함수 실행시 전달하는 인자가 한 개라면 소괄호를 생략할 수 있습니다.
let 함수2 = x => x + 10

// 화살표 함수 내부에서 한 줄 표현식만 반환한다면 return 키워드를 생략해도 됩니다.
let 함수3 = x => x + 10

let 결과 = 함수3(2);

console.log(결과);
```

<aside>
🤔 이런 방식의 익명 함수 표현식을 다른 언어에서는 람다식이라고 부른답니다!

</aside>

1. 즉시실행함수 (IIFE, Immediately Invoked Function Expression)

함수를 정의함과 동시에 즉시 실행하는 방법을 말합니다.

```jsx
(function() {
  console.log('이 함수는 만들어지자마자 바로 실행됩니다!');
})();

(function() {
	document.querySelector(".btn").addEventListener("click", function(){ 
	console.log('click!')
	});
})();
```

또한 즉시실행함수는 코드를 캡슐화하여 모듈화된 코드를 작성할 수 있게 합니다. 이 내용은 함수 심화 과정에서 자세히 다루도록 하겠습니다.

---
## 1. 조건문

조건문은 조건에 따라 실행되는 코드를 말합니다. 조건식이 참(`Truthy`)인 값이나 거짓(`Falsy`)인 값을 반환하는지에 따라 코드를 수행할지 말지 판단합니다.

### 1.1 if문

조건에 따라 실행되는 조건문 중 if문은 가장 많이 사용되는 문법입니다.

아래는 기본적인 if문의 예시입니다.

```jsx

/**
if (조건식) {
  // 조건식이 참일 때 실행될 코드
}
*/

let test=5;
if(test < 10){
	//codes
}

```

중괄호안의 코드가 한 줄 뿐이라면 중괄호를 아래와 같이 생략해서 쓸 수 있습니다.

```jsx
if (true) console.log("중괄호를 생략했습니다.");
```

하지만 코드를 여러사람이 같이 보게 될 경우 가독성을 위해 생략하지 않는 것을 추천합니다.

- **if-else 문**

if문은 조건이 참일 때만 실행되기 때문에, 그 밖의 상황인 조건이 거짓일 때 실행할 코드가 필요한 경우도 필요합니다. 이때 사용하는 것이 else문입니다.

```jsx
let x = 3;
let y = 7;

if(x == y){
  console.log('if문으로 실행되었습니다.');
} else{
  console.log('else문으로 실행되었습니다.');
}
```

- if와 else 를 결합하여 아래처럼 다양한 경우를 대응하도록 코드를 작성할 수 있습니다.

```jsx
let score = 69;
let money = 1000;

if (score > 90){
  document.write('참 잘했습니다!<br>');
  money += 100000
} else if (score > 80){
  document.write('잘했습니다!<br>');
  money += 10000
} else if (score > 70){
  document.write('했습니다!<br>');
  money += 1000
} else {
  money = 0
}

document.write(money);
```

위 코드에서는 `score > 90`이 참을 반환하면 첫 번째 블록 안의 코드가 실행되고, `score > 90`이 거짓을 반환고 `score > 80`가 참일 때는 두 번째 블록 안의 코드가 실행됩니다. 만약 모든 조건식이 거짓을 반환한다면 else 블록 안의 코드가 실행됩니다.

### 1.2 **삼항연산자 (Conditional ternary operator)**

- 조건을 통해 바로 값을 반환하고 싶을 때 사용

삼항연산자는 if-else 문을 간단하게 표현하는 방법입니다. 삼항연산자, 삼항조건연산자, 삼항식 등 여러가지 이름으로 불립니다. 여기서는 삼항연산자로 통칭하겠습니다.

아래는 삼항연산자의 구조입니다.

```jsx
조건식 ? 조건식이 참일 때 실행될 코드 : 조건식이 거짓일 때 실행될 코드
```

위 코드에서 조건식이 참을 반환하면 콜론(:) 앞의 코드가 실행되고, 거짓을 반환하면 콜론 뒤의 코드가 실행됩니다.

코드로 살펴보겠습니다.

```jsx
let item = true ? console.log('true') : console.log('false');
console.log(item);
```

![스크린샷 2022-02-24 오후 8.49.33.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/e8f11927-b70c-4524-9227-a3efac08e7aa/b39bd7f6-739f-4caf-96d7-a388c780958d/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-02-24_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_8.49.33.png)

`item`이라는 변수에 값을 할당하는 삼항연산자입니다. 

true는 Truthy 값이기 때문에  `console.log('true')`가 실행되고 그 반환값이 `item`에 할당됩니다.`console.log`함수는 반환값이 `undefined`이므로 `item`에는 `undefined`가 할당됩니다.

좀 더 쉬운 예제로 살펴보겠습니다.

```jsx
let item = true ? 100 : 200;
console.log(item);
```

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/e8f11927-b70c-4524-9227-a3efac08e7aa/02ebf516-6ab3-4f12-a054-17d448e2fcc5/Untitled.png)

이처럼 삼항연산자는 코드의 실행도 해주고 값으로 사용할 수 있다는 점에서 if문과 다릅니다.

즉, if 문은 특정 코드 구문을 실행하는 문(Statement)이라면, 삼항연산자는 값으로 판단되는 표현식(Expression) 입니다.

if 문과 삼항연산자의 구조를 비교하면 아래와 같습니다.

```jsx
// if-else 문
if (조건식) {
  // 조건식이 참일 때 실행될 코드
} else {
  // 조건식이 거짓일 때 실행될 코드
}

// 삼항연산자
조건식 ? 참일 때 실행될 코드 : 거짓일 때 실행될 코드

```

위 두 예시는 동일한 결과를 반환합니다.

좀 더 구체적인 예시로 비교해보겠습니다.

```jsx
let price = 5000;

let message = (price>6000) ? '비싸요!' : 
							(price<3000) ? '엄청싸요!' : '적당해요!';

// 위의 코드는 아래와 같다.
let price = 5000;
let message = '';

if (price > 6000) {
		message = '비싸요!';
} else if (price < 3000) {
		message = '엄청싸요!';
} else {
		message = '적당해요!';
}
```

위에서 살펴본것 처럼 삼항 조건 연산자는 if문을 간단하게 표현하기 때문에 코드를 가볍게 할 수 있습니다. 하지만, 삼항 조건 연산자가 너무 많은 조건들을 비교할 경우 오히려 if문에 
비해 가독성이 떨어질 수 있으므로 주의해야 합니다.

---
## 1. 조건문

조건문은 조건에 따라 실행되는 코드를 말합니다. 조건식이 참(`Truthy`)인 값이나 거짓(`Falsy`)인 값을 반환하는지에 따라 코드를 수행할지 말지 판단합니다.

### 1.1 if문

조건에 따라 실행되는 조건문 중 if문은 가장 많이 사용되는 문법입니다.

아래는 기본적인 if문의 예시입니다.

```jsx

/**
if (조건식) {
  // 조건식이 참일 때 실행될 코드
}
*/

let test=5;
if(test < 10){
	//codes
}

```

중괄호안의 코드가 한 줄 뿐이라면 중괄호를 아래와 같이 생략해서 쓸 수 있습니다.

```jsx
if (true) console.log("중괄호를 생략했습니다.");
```

하지만 코드를 여러사람이 같이 보게 될 경우 가독성을 위해 생략하지 않는 것을 추천합니다.

- **if-else 문**

if문은 조건이 참일 때만 실행되기 때문에, 그 밖의 상황인 조건이 거짓일 때 실행할 코드가 필요한 경우도 필요합니다. 이때 사용하는 것이 else문입니다.

```jsx
let x = 3;
let y = 7;

if(x == y){
  console.log('if문으로 실행되었습니다.');
} else{
  console.log('else문으로 실행되었습니다.');
}
```

- if와 else 를 결합하여 아래처럼 다양한 경우를 대응하도록 코드를 작성할 수 있습니다.

```jsx
let score = 69;
let money = 1000;

if (score > 90){
  document.write('참 잘했습니다!<br>');
  money += 100000
} else if (score > 80){
  document.write('잘했습니다!<br>');
  money += 10000
} else if (score > 70){
  document.write('했습니다!<br>');
  money += 1000
} else {
  money = 0
}

document.write(money);
```

위 코드에서는 `score > 90`이 참을 반환하면 첫 번째 블록 안의 코드가 실행되고, `score > 90`이 거짓을 반환고 `score > 80`가 참일 때는 두 번째 블록 안의 코드가 실행됩니다. 만약 모든 조건식이 거짓을 반환한다면 else 블록 안의 코드가 실행됩니다.

### 1.2 **삼항연산자 (Conditional ternary operator)**

삼항연산자는 if-else 문을 간단하게 표현하는 방법입니다. 삼항연산자, 삼항조건연산자, 삼항식 등 여러가지 이름으로 불립니다. 여기서는 삼항연산자로 통칭하겠습니다.

아래는 삼항연산자의 구조입니다.

```jsx
조건식 ? 조건식이 참일 때 실행될 코드 : 조건식이 거짓일 때 실행될 코드
```

위 코드에서 조건식이 참을 반환하면 콜론(:) 앞의 코드가 실행되고, 거짓을 반환하면 콜론 뒤의 코드가 실행됩니다.

코드로 살펴보겠습니다.

```jsx
let item = true ? console.log('true') : console.log('false');
console.log(item);
```

![스크린샷 2022-02-24 오후 8.49.33.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/e8f11927-b70c-4524-9227-a3efac08e7aa/b39bd7f6-739f-4caf-96d7-a388c780958d/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-02-24_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_8.49.33.png)

`item`이라는 변수에 값을 할당하는 삼항연산자입니다. 

true는 Truthy 값이기 때문에  `console.log('true')`가 실행되고 그 반환값이 `item`에 할당됩니다.`console.log`함수는 반환값이 `undefined`이므로 `item`에는 `undefined`가 할당됩니다.

좀 더 쉬운 예제로 살펴보겠습니다.

```jsx
let item = true ? 100 : 200;
console.log(item);
```

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/e8f11927-b70c-4524-9227-a3efac08e7aa/02ebf516-6ab3-4f12-a054-17d448e2fcc5/Untitled.png)

이처럼 삼항연산자는 코드의 실행도 해주고 값으로 사용할 수 있다는 점에서 if문과 다릅니다.

즉, if 문은 특정 코드 구문을 실행하는 문(Statement)이라면, 삼항연산자는 값으로 판단되는 표현식(Expression) 입니다.

if 문과 삼항연산자의 구조를 비교하면 아래와 같습니다.

```jsx
// if-else 문
if (조건식) {
  // 조건식이 참일 때 실행될 코드
} else {
  // 조건식이 거짓일 때 실행될 코드
}

// 삼항연산자
조건식 ? 참일 때 실행될 코드 : 거짓일 때 실행될 코드

```

위 두 예시는 동일한 결과를 반환합니다.

좀 더 구체적인 예시로 비교해보겠습니다.

```jsx
let price = 5000;

let message = (price>6000) ? '비싸요!' : 
							(price<3000) ? '엄청싸요!' : '적당해요!';

// 위의 코드는 아래와 같다.
let price = 5000;
let message = '';

if (price > 6000) {
		message = '비싸요!';
} else if (price < 3000) {
		message = '엄청싸요!';
} else {
		message = '적당해요!';
}
```

위에서 살펴본것 처럼 삼항 조건 연산자는 if문을 간단하게 표현하기 때문에 코드를 가볍게 할 수 있습니다. 하지만, 삼항 조건 연산자가 너무 많은 조건들을 비교할 경우 오히려 if문에 비해 가독성이 떨어질 수 있으므로 주의해야 합니다.

### 1.3 s**witch문**

if-else 조건문 외에도, switch 문을 사용하여 여러 조건에 대한 실행 코드를 작성할 수 있습니다. switch case 문은 하나의 변수를 여러 값과 비교하여 실행 코드를 결정하는 조건문입니다.

아래는 switch case 문의 기본 구조입니다.

```jsx
switch (표현식) {
  case 값1:
    // 값1에 대한 실행 코드
    break;
  case 값2:
    // 값2에 대한 실행 코드
    break;
  ...
  default:
    // 모든 case에 해당하지 않을 때 실행될 코드
    break;
}
```

위 코드에서 표현식은 case 문의 값과 비교할 변수입니다. 표현식의 값과 case의 값이 같은 경우 해당 case의 실행 코드가 실행됩니다. 만약 표현식 깂과 모든 case의 값이 일치하지 않는 경우 default 블록 안의 코드가 실행됩니다.

switch문의 특징은 다음과 같습니다.

- switch 뒤에 오는 표현식들의 값에 따라 실행시킬 코드가 있는 곳으로 실행을 옮겨갑니다.
- 코드실행을 한 뒤, break에 의해서 조건문을 빠져나오게 됩니다.
- 표현식이 case와 일치하는 경우가 없다면 default 문으로 이동합니다.
- default 문은 필수가 아닌 선택사항입니다.

switch 문은 표현식의 값과 case의 값이 일치하는 경우에만 실행 코드가 실행됨을 케이스별로 명확히 구분하고 있어서 if 문에 비해 가독성이 좋습니다.

간단한 예시를 살펴보겠습니다.

```jsx
switch (new Date().getDay()) {
  case 1:
    document.write('월요일입니다.');
    break;
  case 2:
    document.write('화요일입니다.');
    break;
  case 3:
    document.write('수요일입니다.');
    break;
  case 4:
    document.write('목요일입니다.');
    break;
  case 5:
    document.write('금요일입니다.');
    break;
  default:
    document.write('금금요일입니다. 주말이 뭐죠?');
    break;
}
```

위 코드에서 switch의 표현식은 자바스크립트 내장 Date() 함수를 통해 현재의 시간정보를 반환하고, getDay() 함수로 시간에서 요일 정보만 추출하고 있습니다.

switch문은 case마다 `break;` 라는 코드를 작성해 주도록 되어있습니다. 만약 해당 코드가 없다면 어떤 결과가 나올까요?

```jsx
let price = 0;
let menu = '카페라떼'; // 메뉴를 바꿔보세요!

switch (menu) {
		case '아메리카노':
				price = 4000;
	  case '카페라떼':
				price = 5000;
		case '바닐라라떼':
				price = 6000;
	  case '콜드브루':
				price = 5500;
		case '딸기라떼':
				price = 7000;
	  case '레몬에이드':
				price = 6500;
		case '에스프레소':
				price = 3500;
	  case '루이보스':
				price = 4500;
		default:
				console.log('메뉴를 정확히 입력하세요.');
}
```

![스크린샷 2022-02-14 오후 2.12.57.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/e8f11927-b70c-4524-9227-a3efac08e7aa/296c5f12-f5dc-4653-9506-be17920a825b/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-02-14_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_2.12.57.png)

default 문이 실행되어 가격이 4500이 된 것을 볼 수 있습니다. **즉, `break`가 없다면 switch문을 탈출하지 않고** 모든 코드들을 순서대로 실행시킵니다. switch문을 적절하게 사용하고 싶다면 반드시 break를 작성해주는 것을 잊지맙시다. 

---
## 2. 반복문

다음에는 반복문에 대해서 알아보도록 하겠습니다.  

먼저 다음과 같은 배열이 존재한다고 가정해 봅시다.

```jsx
const cars = ["BMW", "Volvo", "Saab", "Ford", "Flat", "Audi"];

let text = "";

`
<section>
<h2>BMW</h2>
</section>
<section>
<h2>Volvo</h2>
</section>
...
`
```

여기서 만약 배열 cars에 담긴 내용을 전부 text라는 변수에 넣고 싶다면 어떻게 해야 할까요? 지금까지 배운 내용으로는 다음처럼 길고 반복적인 작업을 통해 text에 배열의 내용을 넣을 수 있습니다.

- 기존 방식 CODE

```jsx
text += '<section><h2>' + cars[0] + '</h2></section>'
text += '<section><h2>' + cars[1] + '</h2></section>'
text += '<section><h2>' + cars[2] + '</h2></section>'
text += '<section><h2>' + cars[3] + '</h2></section>'
text += '<section><h2>' + cars[4] + '</h2></section>'

console.log(text)
// document.body.innerHTML = text
// document.write(text)
```

- 하지만 반복문을 사용하면 아래 코드처럼 간단하게 배열의 내용을 text에 넣을 수 있습니다.

```jsx
const cars2 = ["BMW", "Volvo", "Saab", "Ford", "Flat", "Audi"];
let text2 = ''
for (let i = 0; i < cars2.length; i++) {
    text2 += '<section><h2>' + cars2[i] + '</h2></section>' 
}
text2
```

이렇게 단순한 작업을 여러번 반복해야 할때 사용하는것이 바로 반복문입니다.

이런 반복문 중에 가장 널리 사용되는것이 바로 `for`문입니다.

`for`문은 변수를 선언하는 **초기화식**과, 결과(true or false)에 따라 실행문의 실행 여부를 판단하는 **조건식**, 실행문 이후 변수의 증감을 나타내는 **증감식**으로 구성되어 있다.

```jsx
for(초기화식; 조건식; 증감식) {
	실행문;
}
```

### 2.1 **for 문의 다양한 예시**

```jsx
//반복문
for(var i=0; i<10; i++){
  document.write(i, '<br>');
}

//1부터 100까지의 짝수의 합
let s = 0;
for (var i = 0; i < 101; i+=2) {
  document.write(i, '<br>');
  s += i;
}
document.write(s, '<br>');

//구구단
for (var i = 2; i < 10; i++) {
  for (var j = 1; j < 10; j++) {
    document.write(`${i} X ${j} = ${i*j} <br>`);
  }
}

//100보다 작은 3의 배수와 5의 배수의 합
s = 0;
for (var i = 0; i < 101; i++) {
  if(i%3==0 || i%5==0){
    document.write(i, '<br>');
    s += i;
  }
}
document.write(s, '<br>');
```

```jsx
//평균 구하기
var value1 = [100, 200, 50, 400, 900];
var value2 = [60, 40, 80, 30, 90];
function average(value){
  var sum = 0;
  for(var i=0; i<value.length; i++){
    sum += value[i];
  }
  return sum/value.length;
}

document.write('평균1 : ', average(value1)); //330
document.write('<br>');
document.write('평균2 : ', average(value2)); //60
```

```jsx
//최댓값 구하기
var value = [100, 200, 50, 400, 900];
function maximum(value){
  var max = 0;
  for(var i=0; i<value.length; i++){
    if(max < value[i]){
      max = value[i];
    }
  }
  return max;
}
document.write(maximum(value)); //900
document.write('<br>');

//Math.max.apply() 사용해서 최댓값 구하기
var max2 = Math.max.apply(null, value);
document.write(max2); //900
```

- **for 문의 선택적 사용**

`for`의 구성요소들은 모두 선택적으로 사용할 수 있습니다.

아래 코드처럼 초기화식을 생략하고 for문 밖의 변수를 이용할 수 있습니다.

```jsx
let i = 0;  // 변수 선언
for (; i < 7; i++) {
	console.log('count: ' + i)
}
```

조건식 또한 선택적으로 사용가능하지만 생략할 경우 무조건 true로 평가되기 때문에 코드를 무한히 반복하게 됩니다. 이럴때는 꼭 실행문 안에 별도의 조건문을 넣어 무한루프에 빠지지 않도록 해야합니다.

```jsx
for (let i = 0;; i++) {
	if (i > 7) { console.log(i + '살은 초등학생입니다.' )}
	if (i >= 13) break;
}
```

<aside>
💡 for문의 반복 실행은 break문을 통해 빠져나올 수 있습니다.

</aside>

모든 구성요소를 생략할 경우 역시 무한루프에 빠지게 됩니다.

```jsx
let i = 0;

for(;;) {
		i++;
		console.log('count: ' + i)
		if(i >= 10) break;
}
```

<aside>
💡 `for문` 구성요소 선택적 사용시 주의사항

- 초기화식, 조건식, 증감식을 구분하는 사이의 세미콜론 `;`은 생략이 불가합니다.
- 따라서 모든 구성 요소 생략시, 세미콜론은 반드시 2개 모두 포함되어야 합니다.
</aside>

### **2.2 while 문**

while 문은 주어진 조건식이 참일 때 반복적으로 실행되는 반복문입니다. 

while 문의 구조는 아래와 같습니다.

```jsx
while (조건식) {
  // 조건식이 참일 때 실행될 코드
}
```

조건식은 Truthy 또는 Falsy값을 반환하는 표현식입니다. 만약 조건식이 Truthy를 반환하면 중괄호 안의 코드가 반복적으로 실행되며, 조건식이 falsy 값을 반환하는 순간 반복이 종료됩니다.

예시를 보도록 하겠습니다.

```jsx
let num = 0;

while (num < 11) {
  document.write(num, '<br>');
  num += 1;
}
```

위 코드에서는 변수 num을 0으로 초기화하고, num이 11보다 작을 때까지 반복적으로 실행됩니다. 반복문 안에서는 num의 값이 출력되고, num은 1씩 증가합니다.

- **do-while 반복문**

do-while 반복문은 조건식이 거짓이더라도 반복문이 최소한 한 번은 실행되어야 할 때 사용됩니다. 

이렇게 동작되는 이유는 while 반복문과 다르게, 조건식이 반복문 안의 코드 실행 이후에 평가되기 때문입니다. 따라서 do-while 반복문을 사용하면 최소한 한 번의 실행이 보장됩니다. 예를 들어, 사용자로부터 입력을 받는 코드를 작성할 때, 아래처럼 do-while 반복문을 사용하여 최초 한 번은 입력을 받도록 할 수 있습니다.

```jsx
let input;

do {
  input = prompt("숫자를 입력하세요.");
} while (isNaN(input));

console.log("입력한 숫자는 " + input + "입니다.");

```

따라서 우리가 앞서 while 문에서 사용했던 코드의 조건식을 do-while 문에서 고치면 아래와 같습니다. 

```jsx
let num = 0;

do {
  document.write(num, '<br>');
  num += 1;
} while (num < 11);
```

### **2.3 반복문의 break & continue**

앞서 for문에서 잠시 살펴봤듯, 조건에 따른 종료 이전에 사용자의 개입으로 좀 더 빠른 종료를 원하면 `break` 를 사용하여 반복문에서 나올 수 있습니다. `break`문으로 반복문이 종료되면 그 다음 코드가 차례로 실행됩니다. break 문은 switch 문 만의 전유물이 아니랍니다 🙂

```jsx
// 예시 1
let num = 0;
while (num < 11) {
 num++;
 document.write(num, '<br>');
 if(num > 5){
   break;
 }
}

// 예시 2
let i = 0;
while (i < 100) {
		i++;
	if (i === 14) {
			console.log(i + '살 부터 중학생이 됩니다.');
			break;
	}
}
console.log('중학교 입학을 축하합니다');
```

또한 `continue`문은 반복문을 완전히 빠져나가는 `break`와 다르게 반복문의 다음 반복으로 이동합니다.

아래의 예시 코드를 보면, 변수 `i` 가 13보다 작다는 조건문에서 `continue` 가 실행되기 때문에 해당 조건의 반복을 넘어서 다음 반복으로 이동합니다. 따라서 **if 조건문에서 falsy 값을 반환하는** 13 이상의 변수 값부터 `console.log(i + '살은 청소년입니다.')` 가 실행됩니다.

만약 `continue`가 실행되지 않았다면 `0살은 청소년입니다.` 부터 `19살은 청소년입니다.`가 모두 실행되었겠죠 🙂

```jsx
for (let i = 0; i < 20; i++) {
		if (i < 13) continue;
		console.log(i + '살은 청소년입니다.');
}
```