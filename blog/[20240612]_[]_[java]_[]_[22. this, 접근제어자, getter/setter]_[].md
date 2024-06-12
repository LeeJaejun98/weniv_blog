# 자바의 this

- 현재의 객체를 참조
- 현재 객체의 멤버 변수 & 메서드에 접근 가능
- 용도
    - 같은 이름의 지역변수 / 멤버 변수 있을 때 ⇒ this 사용시 멤버 변수에 접근 가능
    - 다른 메서드를 호출하기 위해 사용
    
    ```java
    public class Person {
        // 멤버 변수
        String name;
        int age;
    
        // 생성자
        public Person(String name, int age) {
            this.name = name;
            this.age = age;
        }
    
        // 메서드
        public void sayHello() {
            System.out.println("Hello, my name is " + this.name);
        }
    
        public void introduce() {
            System.out.println("I am " + this.age + " years old.");
        }
    }
    
    ```
    

---
# final / static final

## 1. final field

- 초기값 지정시 프로그램 실행 도중 수정 X

```java
final 타입 필드명 [= 초기값];
```

- 그렇다면 초기값은 언제 줄수 있을까?
    1. 필드 선언시 ( 단순 값일 때 )
    2. 생성자에서 초기화 ( 외부 데이터로 초기화 해야 할 때 )

```java
public class Person {
	final String nation = "Korea";
	String name;

	public Person(String name) {
		this.name = name;
	}
}
```

```java
public class PersonExample {
	public static void main(String[] args) {
		Person person = new Person("계백");

		System.out.println(person.nation);
		System.out.println(person.name);
		
	  person.nation = "을지문덕";   // Error: 컴파일 오류 발생. final 필드는 값 수정 불가
	}
	
}
```

 ⇒ 오류의 이유:

- Person클래스에서 final로 선언한 nation을 외부 클래스에서 변경 시도했기 때문

## 2. 상수 ( static final )

1. 자바에서의 상수란?
    
    ⇒ 원주율 파이, 지구의 무게및 둘레같이 불변의 값을 저장하는 필드
    
2. final과 static final의 차이?
    
    ⇒ final : 객체마다 저장 및 생성자 매개변수로 여러 값을 가질수 있다
    
    ⇒ static final : 객체마다 저장할 필요 X (공용성) , 여러 값으로 초기화 X
    
3. 선언

```java
static final 타입 상수[= 초기값];
```

1. 특징
    1. 객체마다 저장 X ⇒ 클래스에만 포함
    2. 초기화시 변경 X
    3. 모두 대문자로 적어주는게 컨벤션, 여러 단어라면 ( _ ) 사용
    
    ex )
    
    ```java
    public class Earth {
    	static final double EARTH_RADIUS = 6400;
    	static final double EARTH_SURFACE_AREA;
    
    	static {
    		EARTH_SURFACE_AREA = 4 * Math.PI * EARTH_RADIUS * EARTH_RADIUS;
    	}
    }
    ```
    
---
# 접근 제어자

- 변수 || 매소드의 사용권한을 설
- 종류 ( 접근 범위 작은것 부터 )
    - private
        - 해당 클래스 안에서만 접근 가능
    - default
        - 접근 제어자 별도 설정 X default로 자동 설정,  동일 패키지 안에서만 접근 가능
    - protected
        - 동일 패키지의 클래스 || 해당 클래스를 상속 받은 클래스만 접근 가능
    - public
        - 전체 클래스에서 접근 가능

| 접근 제어자 | 같은 클래스 | 같은 패키지 | 자식 클래스 | 전체 |
| --- | --- | --- | --- | --- |
| public | O | O | O | O |
| protected | O | O | O |  |
| default(packege-private) | O | O |  |  |
| private | O |  |  |  |

---

# Getter / Setter

## Setter

- 객지프 = 데이터에 대한 외부에서의 직접적인 접근을 막음
    - 객체의 무결성을 깰수 있기 때문

 ⇒ 따라서 메소드를 통해 데이터 변경하는걸 선호

- 데이터에 대한 외부에서의 접근을 막고, 메소드를 공개해 메소드를 통한 접근 유도
    - why?
        
        ⇒ 메소드 : 매개값 검증을 통해 유효한 값만 데이터로 저장할 수 있게 함
        
- 예제

```java
public class Car {
		private int speed;
		
		public void setSpeed(int speed) {
				if (speed < 0) {
						this.speed = 0;
				} else {
						this.speed = speed;
				}
		}
}
```

## Getter

- 객체 외부에서 객체의 필드 값을 사용하기 부적절할수도 있기 때문에
- 메소드를 통해 가공 후 외부로 전달

**클래스 선언시 유의 사항**

1. 필드 값은 private ⇒ 외부로부터의 직접적 접근 방지
2. 필드에 대한 Getter/Setter 메소드 작성 ⇒  필드값 안전하게 변경/사용

field type이 boolean값이라면?

- Getter의 경우 : “get”을 사용하지 않고 “is” 사용
- ex)

```java
private boolean stop;

public boolean isStop(){
	return stop;
}

public void setStop(boolean stop){
	this.stop = stop;
}
```