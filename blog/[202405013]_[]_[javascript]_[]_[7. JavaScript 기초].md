# 동적인 웹을 위해 자바스크립트가 할 수 있는 것들

1. **데이터를 저장하다**
    - 저장 공간 : var , let , const
    - 저장할 값의 형태 : 숫자, 문자열, 빈 값(null, undefined), boolean(true, false), 배열, 객체
    - 코드의 뭉치 : 함수

1. **값을 계산하다**
    - 사칙연산
    - 논리연산
    - 조건문
    - 반복문
    - 자료형의 내장함수

1. **결과를 반영하다**
    - DOM & BOM API

1. **다른 컴퓨터와 통신하다**
    - Ajax

## 1.4 JavaScript를 사용하는 여러가지 방법들

- HTML 파일 내부 삽입하기
    
    HTML내에 javascript를 포함하고 로드합니다. 
    
    1. HTML 태그 내 삽입 (권장 하지 않음)
        
        ```markdown
        <button onclick="window.alert('hello world');">hello</button>
        ```
        
    2. script 태그를 통해 삽입 ( 이방법을 제일 많이 씀 )
        
        ```markdown
        <!DOCTYPE html>
        <html lang="ko">
        <head>
        </head>
        <body>
            <script>
                window.alert('hello world!');
            </script>
        </body>
        </html>
        ```
        
    
- HTML 파일 외부에 있는 스크립트 파일을 로드
    
    외부 파일로 저장을 하고 로드합니다.
    
    ```markdown
    <!DOCTYPE html>
    <html lang="ko">
    <head>
    </head>
    <body>
        <script src="test.js"></script>
    </body>
    </html>
    ```
    

**브라우저 콘솔창**

크롬 브라우저의 콘솔창은 `Ctrl + Shift + i` 버튼을 누르면 나오는 창입니다. 다음은 크롬에서 **`about:blank`** 페이지에 접속한 화면입니다. 

이 페이지는 비어있는 페이지이며 간단한 javascript 연습을 하기 충분합니다.

!https://prod-files-secure.s3.us-west-2.amazonaws.com/e8f11927-b70c-4524-9227-a3efac08e7aa/86cef87d-9480-47e1-b306-55b52b68971a/Untitled.png

---

# 변수

## 2.1 변수란?

변수는 **‘변할 수 있는 수’, ’변할 수 있는 정보’**라는 뜻입니다.

프로그램을 만들때는 필요한 숫자나 문자와 같은 데이터를 보관할 공간이 필요한데, 이러한 공간에 들어가는 데이터가 무엇인지 이름을 붙이는 포스트잇 같은 역할을 하는 것이 변수입니다. 

<aside>
💡 변수의 왼쪽 `x, y, z`값과 오른쪽 `3, 4, 5`값은 모두 메모리 상에 올라갑니다.

```jsx
var x = 3;
let y = 4;
const z = 5;
```

</aside>

변수는 선언하고, 할당하고, 사용할 수 있습니다. 또한, 변수는 ‘변할 수 있는 수’이므로 const를 제외하고 지정된 **값을 계속 바꿀 수 있습니다.**

```html
<!DOCTYPE html>
<html>
<head>
	<title>변수</title>
</head>
<body>
	<script>
	    let 나변수 = 10; // 1번
      나변수 = 20; // 2번
      나변수 = 30; // 3번
	</script>
</body>
</html>
```

![견고한 JS.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/e8f11927-b70c-4524-9227-a3efac08e7aa/9d526a4c-ecf1-4203-872c-688908aae641/%EA%B2%AC%EA%B3%A0%ED%95%9C_JS.png)

**변수명을 정할 때** 

- 변수이름은 $, _ 를 제외한 공백, 특수문자, 구두점(글의 여러 가지 경계를 구분하기 위해 사용되는 반점(,), 온점(.), 물음표(?) 등등…)을 사용할 수 없습니다.
- 첫 글자는 숫자가 될 수 없습니다.
- 대소문자를 구별합니다.
- [예약어](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Lexical_grammar#reserved_words)가 쓰일 수 없습니다.
- 유니코드 문자도 사용할 수 있습니다. 그러나 실무에는 보통 영어를 사용합니다.

**변수의 특징**

- 변수를 선언 할 때는 var, let, const의 키워드를 사용할 수 있습니다. var, let 두 가지 키워드는 변수를, const 키워드는 변경할 수 없는 수 즉, 상수를 의미합니다.
- var, let, const 키워드는 변수를 선언 할 때 한번만 사용합니다.
- var 키워드는 초기화가 필요 없고 재할당이 가능합니다. 또한 생략할 수도 있습니다. 하지만 var 키워드가 생략된 변수는 엄격모드(strict mode)에서는 에러가 발생됨으로 권장되지 않습니다.
- let과 const는 블록-레벨 선언으로 불리며, 선언된 코드 블록 밖에서 접근할 수 없으며 재정의가 불가능한 특징을 가지고 있습니다. 특히 const 의 경우에는 반드시 초기화가 필요합니다.

```jsx
'use strict';  // 자바스크립트를 엄격모드에서 실행

valueA;        // 변수 키워드 생략은 엄격모드에서 에러발생!
var valueA;
var valueA;
let valueA;    // 재정의로 인한 에러발생!
const my_name; // 초기화가 없어서 에러발생!
```

변수를 할당하는 방법은 다음과 같습니다.

```jsx
valueA = 1;
const my_name ="WADE";

if(true){ // -- 코드블록의 시작입니다. -- //

	let valueB = 'Hello!';
	const my_name ="WADE";       // 코드블록 밖의 my_name과 별개의 상수입니다.

} // -- 코드블록의 끝입니다. -- //

valueB = 'nice to meet you!';  // 변수 정의 이전에 값을 할당 할 수 없습니다!
let valueB = 'Hi!';            // 코드블록 안의 valueB와 별개의 변수입니다.
```

<aside>
💡 **let 과 const. 언제 사용해야 할까요?**

JavaScript에서 **`let`**과 **`const`**는 모두 변수를 선언하는 키워드입니다. 그러나 두 키워드는 서로 다른 용도를 가지고 있으며, 상황에 따라 선택할 수 있습니다.

**`let`**은 재할당이 가능한 변수를 선언할 때 사용됩니다. 이것은 변수의 값이 언제든지 변경될 수 있다는 것을 의미합니다. **`let`** 변수는 블록 스코프를 가지므로, 변수를 선언한 블록 안에서만 유효합니다.

반면에 **`const`**는 재할당이 불가능한 상수를 선언할 때 사용됩니다. 이것은 변수의 값이 한 번 할당되면 변경될 수 없다는 것을 의미합니다. **`const`** 변수도 **`let`**과 마찬가지로 블록 스코프를 가집니다.

그러나 **`const`**를 사용하는 것이 더 좋은 경우가 많습니다.

1. 의도하지 않은 값의 변경을 방지할 수 있습니다.
    
    **`const`**를 사용하면 변수의 값이 한 번 할당되면 변경될 수 없습니다. 따라서 의도하지 않은 값의 변경을 방지할 수 있습니다. 이것은 코드의 예측 가능성을 높이며, 따라서 버그를 줄일 수 있습니다.
    
2. 가독성을 높일 수 있습니다.
    
    **`const`**를 사용하면 다른 개발자들이 변수의 값이 변경될 가능성이 없다는 것을 빠르게 인지할 수 있으며, 반드시 초기화를 해야하기 때문에 어떤 데이터가 사용되는지 초기에 확인 할 수 있습니다. 이것은 코드의 가독성을 높이고 유지 보수성을 향상시킵니다.
    

그러나 변수의 **가리키는 값**이 반드시 변경되어야 하는 경우에는 **`let`**을 사용해야 합니다. 예를 들어 +, - 같은 연산자에 의해 할당된 값이 변경되야 할 경우가 있습니다. 따라서 **`const`**와 **`let`**을 적절하게 사용하여 코드를 작성하는 것이 중요합니다.

</aside>

<aside>
🤔 블록 스코프 (block scope)
자바스크립트 문법에는 여러줄의 코드를 하나로 묶어주는 단위인 블록( { } )이 존재합니다.
블록 스코프란 그러한 블록 안에서만 유효한 코드의 범위를 의미합니다. 자세한 내용은 스코프 시간에 자세히 다루도록 하겠습니다! 여기서는 *‘코드에도 사용가능한 범위라는게 있구나’* 하고 이해해 주시면 되겠습니다. 🙂

</aside>

<aside>
🧐 가리키는 값이라고 굵은 글자로 표시한 이유?
아래와 같이 배열 값이 변경이 되더라도 Error가 나지 않는 이유는 값이 추가되더라도 values가 가리키고 있는 값은 그대로 해당 배열이기 때문에 그렇습니다. 화살표는 변하지 않습니다.

```jsx
const values = []; // 1번

values.push(10); // 2번
```

- 1번과 2번의 화살표를 예상해보세요.
    
    
    ![잘못된 화살표](https://prod-files-secure.s3.us-west-2.amazonaws.com/e8f11927-b70c-4524-9227-a3efac08e7aa/9f7d4b4e-efb2-4b4b-b023-6922cd635e71/Untitled.png)
    
    잘못된 화살표
    
    ![올바른 화살표](https://prod-files-secure.s3.us-west-2.amazonaws.com/e8f11927-b70c-4524-9227-a3efac08e7aa/4cb18044-41d1-4188-b94c-97dce07684d6/Untitled.png)
    
    올바른 화살표
    
</aside>