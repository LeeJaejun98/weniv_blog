## Type 이란 ?
- 데이터를 **용도에 맞게 쓰기 위해서 사용**
- 데이터가 앞으로 어떻게 처리될지를 정하게 합니다.

타입은 단순한 데이터를 저장하는 **원시타입**, 그리고 객체로서 저장되는 **참조타입**으로 크게 구별할 수 있습니다. 

<aside>
💡 보통 프로그래밍 언어에서는 변수의 자료형과 함께 변수를 선언하지만 자바스크립트는 자료형을 함께 쓸 필요는 없습니다.

</aside>

```java
String str = "Java"; // Java의 변수 선언식
System.out.println(str);
```

## 1. 원시타입 (Primitive Types)

- 불변의 값을 가짐
- 주소로 저장 (포인터 같은거임)

```jsx
let str1 = 'hello';
let str2 = str1;
console.log(str2); // 'hello'

str1 = 'world';
console.log(str2); // str2에 할당된 값은 여전히 'hello' 입니다.
```

- string, number, bigint, boolean, undefined, symbol, null

<aside>
🧐 원시타입은 str2입장에서 str1의 값을 바꿀 수는 없습니다. 참조타입은 str2입장에서 str1의 값을 바꿀 수 있습니다.

</aside>

## 2. 객체타입 (Object Types)

객체타입의 특징은 

1. 객체는 프로퍼티로 값과 메서드를 가지며, 이 둘은 각각 객체의 상태와 동작을 나타냅니다.
2. **값의 위치**가 저장된다는 점입니다. 객체 값을 다른 변수에 할당 할때는 **값의 참조(위치)**가 저장됩니다.

```jsx
let arr1 = [1, 2, 3];
let arr2 = arr1;
console.log(arr2);

arr1[0] = 10;
// arr1 = [10, 20];
console.log(arr2);

// 비교해보세요.
let value1 = 10;
let value2 = value1;
console.log(value2);

value1 = 20;
console.log(value2);
```

## 배열 (Array) (배열 밖의 것을 뽑아오면 undefined)
- **개념**: 배열(Array)은 데이터를 순서대로 저장하는 객체입니다. 하나의 데이터를 표현하는 원시타입과 달리 여러개의 데이터를 한 변수에 저장할 수 있기 때문에 데이터를 추가하거나, 제거, 정렬, 검색 등 다양한 작업을 수행할 수 있도록 여러가지 메소드를 제공합니다.

**배열의 메소드**

1. shift()와 unshift() ( 이걸로 queue 생성 가능하기도 하다 )

shift() 메소드는 배열에서 첫 번째 요소를 꺼내고 반환합니다, unshift() 메소드는 배열의 첫 번째 요소로 새로운 요소를 추가합니다

```jsx
const myArray = ["사과", "바나나", "수박"];
myArray.shift();
console.log(myArray); 
myArray.unshift("오이", "배");
console.log(myArray);
```

1. splice() ( 시작 인덱스, 삭제할 요소 수, 추가할 요소들… )

```jsx
const arr = [1, 2, 3];
arr.splice(1, 0, 4);
console.log(arr); // [1, 4, 2, 3]
arr.splice(2, 1, 5);
console.log(arr); // [1, 4, 5, 3]
```

1.  slice()

배열에서 요소들을 추출하여 새로운 배열로 반환

slice(추출을 시작할 인덱스, 추출을 끝낼 인덱스)

- 두번째 생략 가능 & 더 크면 배열 끝까지 출력

```jsx
const myArray = ["apple", "banana", "cherry", "durian", "elderberry"];
console.log(myArray.slice(1, 4)); 
console.log(myArray.slice()); 
console.log(myArray.slice(0, 10));
```

1. sort()  ( 정렬 알고리즘에 대한 표준이 없음 )

```jsx
const nums = [3, 1, 8, 6];
console.log(nums.sort());

const nums2 = [23, 5, 1000, 42];
console.log(nums2.sort());

```

!!!! 숫자를 정렬하려고 하면 의도와는 다르게 정렬이 되는데요 !!!!
이때 정렬 방식은 원소를 문자열로 전환한 후에 유니코드 포인트(https://en.wikipedia.org/wiki/List_of_Unicode_characters)의 순서대로 변환하기 때문입니다.(포인트 : 문자에 부여한 고유한 16진수 숫자값)

⇒ 숫자 sort 해결하기 위해 → 비교 함수(compareFunction)를 사용

```jsx
const num3 = [13, 9, 10];

num3.sort(function (a, b) {
  console.log('a: ' + a, 'b: ' + b);
  return a - b;
});
/**
"a: 9"
"b: 13" // a - b는 음수임으로 a를 앞으로 => [**9**, **13**, 10]

"a: 10"
"b: 9" // a - b는 양수임으로 b를 앞으로 => [**9**, 13, **10**]

"a: 10"
"b: 13" // a - b는 음수임으로 a를 앞으로 => [9, **10, 13**]

"a: 10"
"b: 9" // a - b 는 양수임으로 b를 앞으로 => [**9**, **10,** 13]
*/
```

---

<aside>
💡 Tim sort 알고리즘
JavaScript 의 sort 메소드가 원소를 정렬하는 방법은 Tim sort 알고리즘이라고 합니다.(Tim Peters라는 이름의 개발자가 만들었습니다.)
Tim sort는 합병 정렬(Merge sort)과 삽입 정렬(Insertion sort)의 아이디어를 결합한 알고리즘으로 매우 안정적으로 동작하기 때문에 파이썬과 자바 등 다른 언어에서도 널리 사용되는 방법입니다.

데이터를 여러 개의 덩어리로 분할하고, 이 덩어리들을 삽입 정렬 알고리즘으로 정렬한 다음, 합병 정렬 알고리즘을 이용해 정렬된 덩어리들을 하나로 합칩니다. 이렇게 분할하고 정렬하는 과정에서, 이미 정렬된 데이터를 인식하고 이를 활용함으로써 평균적인 수행 시간을 크게 줄일 수 있습니다.
참고 : https://d2.naver.com/helloworld/0315536

</aside>

---

1. forEach() **생각보다 중요!!**

forEach() 메소드는 배열의 각 요소에 대해 주어진 함수를 실행합니다. 이 때, 함수는 인자로 배열 요소, 인덱스를 받습니다. forEach() 메소드는 배열의 요소를 순환하면서 해당 요소를 함수로 전달하고, 이 함수가 각 요소에 대해 실행됩니다.

```jsx
const arr = ['참외', '키위', '감귤'];
arr.forEach(function(item, index) {
  console.log(item, index);
	arr[index] = index;
});

// 결과
// 참외 0
// 키위 1
// 감귤 2
```

forEach() 메소드는 배열의 각 요소에 대해 특정 작업을 수행할 때 사용됩니다. 예를 들어, 배열의 각 요소를 이용하여 다른 배열을 만들거나, 요소를 삭제하거나, 값을 변경하는 등의 작업을 수행할 수 있습니다.

```jsx
const avengers = ['spiderman', 'ironman', 'hulk', 'thor'];

const newAvengers = [];
avengers.forEach(function (item) {
    newAvengers.push('💖' + item + '💖');
});
```

1. map() ( 데이터를 뽑을 때  많이 사용한다)
- 배열의 각 요소에 대해 주어진 함수를 실행하고, 그 결과를 새로운 배열로 반환

```jsx
const arr = [1, 2, 3];
const newArr = arr.map(function(item, index) {
  return item * index;
});

console.log(newArr);
```

map() 메소드의 첫 번째 인자로는 배열의 각 요소를 처리할 함수를, 두번째는 요소의 인덱스를 전달합니다. 이 함수는 배열의 각 요소를 매개변수로 받아 처리한 후, 그 결과를 반환합니다.
<aside>
💡 forEach()와 map()은 별로 다르지 않아보여요!
맞습니다. forEach()와 map()은 둘 다 배열의 각 요소에 대해 주어진 함수를 실행합니다. 하지만 forEach 메소드의 경우 반환값이 없지만 map 메소드는 새로운 배열을 반환한다는 차이가 있습니다.
이러한 차이점은 배열의 원소를 변경하여 새로운 배열을 반환하고자 할때 더 잘 드러납니다.

</aside>

→ 배열 안에 객체에서 데이터를 뽑는 형태로도 사용

```jsx
const data = [
    {
        "_id": "642ba3980785cecff3f39a8d",
        "index": 0,
        "age": 28,
        "eyeColor": "green",
        "name": "Annette Middleton",
        "gender": "female",
        "company": "KINETICA"
    },
    {
        "_id": "642ba398d0fed6e17f2f50c9",
        "index": 1,
        "age": 37,
        "eyeColor": "green",
        "name": "Kidd Roman",
        "gender": "male",
        "company": "AUSTECH"
    },
    {
        "_id": "642ba39827d809511d00dd8d",
        "index": 2,
        "age": 39,
        "eyeColor": "brown",
        "name": "Best Ratliff",
        "gender": "male",
        "company": "PRISMATIC"
    }
];

const ages = data.map((item) => item.age);
```

1. filter()
- 특정 조건을 만족하는 요소들만 추출하여 새로운 배열을 만듬

```jsx
const arr = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
const newArr = arr.filter(function(el) {
  return el % 2 === 0;
});

console.log(newArr);
```

```jsx
const arr11 = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
const newArr = arr11.filter(el => el % 2 === 0);

console.log(newArr);
```

filter() 메소드는 배열에서 특정한 숫자나 날짜 등의 필요한 정보를 가진 원소만 추출할 때 매우 유용한 메소드입니다.

1. includes

요소가 포함이 되어 있으면 true 아니면 false를 반환합니다. 

```jsx
const arr1 = ['hello', 'world', 'hojun']
arr1.includes('world')

const arr1 = ['hello', 'world', 'hojun']
arr1.includes('leehojun')

const arr1 = ['hello', 'world', 'hojun']
arr1.includes('jun')
```

### 2. 객체 (Object)

- 개념 : 여러개의 데이터를 한 변수에 저장할 수 있는 자료형
- 배열과의 차이점
    - 배열 = 배열 생성 시 자동으로 부여되는 인덱스 번호를 이용
    - 객체 = Key - value 값으로 사용

## **객체의 특징**

1. 객체 이름  + “.” + 속성 
    
    ```jsx
    console.log(`${babaYaga.name} from ${babaYaga.from}`);
    console.log(`${babaYaga['name']} from ${babaYaga['from']}`);
    ```
    

1. 객체에 속성을 추가하기 위해서는 객체 이름 뒤에 점(.)과 새로운 속성 이름을 입력하고, 새로운 값을 할당합니다.
    
    ```jsx
    babaYaga.job = "Killer";
    ```
    
    객체에서 속성을 삭제하려면 delete 키워드를 사용합니다.
    
    ```jsx
    delete babaYaga.job;
    ```
    
    in 연산자를 이용해 특정 프로퍼티가 객체안에 존재하는지 알 수 있습니다.
    
    ```jsx
    console.log('age' in babaYaga);
    console.log('mercy' in babaYaga);
    ```