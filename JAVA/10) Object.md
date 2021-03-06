# 객체

객체는 속성과 동작으로 구성되어있다. 자바는 이 속성과 동작을 각각 필드와 메소드라고 부른다.

**객체간의 관계**

1. 집합 관계
2. 사용 관계
3. 상속 관계

## 객체지향 특징

### 추상화

여러 객체에 공통으로 사용되는 내용을 뽑아내는 것을 말한다.

여러 라면이 있다. 물을 끓이고 스프를 넣는 과정은 똑같지만 떡을 넣거나 만두를 넣는 것은 다 다르다. 여기서 공통된 조리법을 골라 부모클래스로 만드는 것이 추상화이다.

### 캡슐화

외부 객체는 객체 내부의 구조를 알지 못한다. (객체가 노출하지 않는 이상.)

필드와 메소드를 캡슐화 하는 이유: 외부의 잘못된 사용으로 객체가 손상되지 않도록하기 위해.

#### 접근 제어자

1.  private

   해당 클래스 내부에서만 사용할 수 있다. 클래스 생성 불가. (클래스 생성: private class 클래스명)

2. default

   변수 앞에 아무것도 정의하지 않으면 붙는다. 같은 패키지 내에서만 접근이 가능하다.

3. protected

   default + 외부 패키지에서는 자신의 자식 클래스만 접근이 가능하다.  생성자 호출은 super()로만 가능하다. 클래스 선언 불가.

4. public

   protected + 다른 패키지에서도 접근이 가능하다.

### 상속성

상위 객체가 자신이 가지고 있는 필드와 메소드를 하위 객체에게 물려주는 것. 

### 다형성

하나의 타입에 여러 객체를 대입하는 것. 동일한 타입을 사용하지만 다양한 결과가 나오는 성질.자바는 다형성을 위해 부모 클래스의 타입 변환을 허용한다. 

## 클래스

클래스에는 객체를 생성하기 위한 필드와 메소드가 정의되어 있다. 

인스턴스: 클래스로부터 만들어진 객체. 

인스턴스화: 클래스로부터 객체를 만드는 과정.

인스턴스 멤버: 객체(인스턴스)를 생성한 후 사용할 수 있는 필드와 메소드. 인스턴스 필드, 인스턴스 메소드라고 부름.

인스턴드 필드는 객체마다 따로 존재하지만 인스턴드 메소드는 메소드 영역에 저장되어 공유된다. 

### 클래스 선언

파일 이름과 동일한 이름의 클래스 선언에만 public 접근 제한자를 붙일 수 있다.

### 클래스 용도

1. 라이브러리 (API)

   다른 클래스에서 이용할 목적으로 설계된다.

2. 실행용

   main() 메소드 제공. 단 하나이다.


### 추상 클래스

추상 클래스는 객체를 생성할 수 없다. 추상 클래스와 실체 클래스는 상속의 관계를 가지고 있다. 추상 클래스는 extends 뒤에만 올 수 있다. 

**선언**

abstract를 붙이면 new연산자를 이용해 객체를 만들지 못하고 상속을 통해 자식 클래스만 만들 수 있다.

```java
public abstract class 클래스 {
    //필드
    //생성자, 자식 객체 생성 시 super() 호출
    //메소드
}
```

### 객체 생성

new 연산자는 힙 영역에 객체를 생성시킨 후 객체의 주소를 리턴한다. 이 주소를 참조 타입인 클래스 변수에 저장하고, 그 변수를 통해 객체를 생성한다. new() 연산자 뒤에는 클래스() 형태인 생성자가 온다.

```java
클래스 변수; //클래스 변수 선언
변수 = new 클래스(); // 객체 생성

클래스 변수 = new 클래스(); //한 개의 실행문으로 작성
```

------

### 클래스 구성 멤버

```java
public class 클래스
{
	int fieldname; //필드, 객체의 데이터가 저장되는 곳
	
	ClassName(){...} //생성자, 객체 생성 시 초기화 역할
	
	void methodName(){...} //메소드, 객체의 동작에 해당하는 실행 블록
}
```

#### 1. 필드

객체의 고유 데이터를 저장하는 곳. 선언 형태는 변수와 비슷하지만 필드를 변수라고 부르지는 않는다. 필드는 생성자와 메소드 전체에서 사용되며 객체가 소멸되지 않는 한 존재한다.

##### 필드 선언

생성자와 메소드 중괄호 블록 내부에서는 선언 할 수 없다. (로컬 변수가 됨.)

```JAVA
타입 필드 = 초기값;
// 초기값 생략 가능. 타입은 기본타입과 참조타입 모두 올 수 있음
```

##### 필드 사용

클래스 외부에서 사용할 경우 객체를 우선 생성해야 한다. 객체 생성 후에는 도트(.) 연산자를 사용해서 필드(나 메소드에) 접근할 수 있다.

#### 2. 생성자

new 연산자로 객체를 생성할 때 호출(항상 실행된다.). 필드를 초기화하거나 메소드를 호출해서 객체를 사용할 준비를 한다. 생성자를 실행시켜야 객체를 만들 수 있다. 

메소드와 다른 점: 클래스 이름으로 되어 있고 리턴 타입이 없다.

##### 기본 생성자

클래스 내부에 생성자 선언을 생략하면 컴파일러는 기본 생성자를 바이트 코드에 자동 추가한다. new 연산자 뒤에도 기본 생성자를 호출해 객체를 생성시킬 수 있다.

```java
클래스() {} //기본생성자
```

##### 생성자 선언 (명시적 생성자)

```java
클래스(매개변수선언,...){객체의 초기화 코드}
```

클래스에 생성자 선언이 있으면 반드시 선언된 생성자를 호출해서 객체 생성을 해야 하고, 기본 생성자를 호출해서 객체를 생성할 수 없다. 매개변수선언은 생략할 수 있다.

```java
public class Car
{
    //생성자
	Car(String color, int cc){ }
}
public class CarEX
{
    public static void main(String[] argc)
    {
        Car myCar = new Car("검정",3000);
        //Car mayCar = new Car(); 기본생성자 사용 불가
    }
}
```

```java
public class Korean
{
    //필드
	String nation="대한민국"; //필드를 선언할 때 초기화
    String name;
    String ssn;
    //생성자
    public Korean(String name, String ssn)
    {
        this.name=name; //생성자의 매개값으로 값을 받아 초기화
        this.ssn=ssn;
    }
}
```

초기화 방법은 필드를 선언 할 때 초기값을 주는 것과 생성자에서 초기값을 주는 것 두 가지가 있다.

[^this.]: 객체 자기 자신의 참조이다.

##### 오버로딩

생성자 오버로딩이란 매개 변수를 달리하는 생성자를 여러 개 선언하는 것이다.

```java
public class Car //오버로딩 예시
{
	Car(){...};
	Car(String model){...};
	Car(String model, String color){...};
	// 매개 변수의 타입, 개수, 순서가 다르게 선언
}
```

오버로딩 사용시 초기화 내용이 중복될 수 있다. 이 경우 한 생성자에 초기화 내용을 작성하고 나머지 생성자는 이 **생성자를 호출**할 수 있다.

##### this() 

다른 생성자를 호출하는 코드. 생성자의 첫줄에만 허용된다. 

```java
public class Car
{
    String model;
    String color;
    int maxSpeed;
    
    Car(String model)
    {
        this(model,"은색",250); //호출
    }
    Car(String model, String color)
    {
        this(model,color,250); //호출
    }
    Car(String model, String color, int maxSpeed)
    {
        this.model = model;
        this.color=color;
        this.maxSpeed=maxSpeed; //공통 실행 코드들
    }
}
```



#### 3. 메소드

객체들 사이의 동작 상요작용. 

##### 메소드 선언

```java
리턴타입 메소드이름([매개변수선언,...])
{
	실행코드 
}
```

리턴타입이 없는 메소드는 void가 온다. 

##### 메소드 호출

리턴값이 없으면 리턴값은 저장하지 않는다.

```java
//내부클래스에 있는 메소드 호출
타입 리턴값저장변수 = 메소드(매개값1,...); 
//외부클래스에 있는 메소드 호출
우선 객체 생성
타입 리턴값저장변수 = 객체.메소드(매개값1,...);
```

##### ... 선언

매개변수의 수를 모를 경우 매개변수를 배열으로 선언한다.  하지만 이 경우 메소드 호출 전 배열을 생성해 줘야 한다. 

```java
int sum1(int[] values){} //메소드

int[] values={1,2,3}; 
int result=sum1(values);
int result=sum1(new int[] {1,2,3,4,5});
```

이 경우 ...을 사용해 선언하면 넘겨준 값의 수에 따라 자동으로 배열이 생성된다.

```java
int sum2(int ... values){}

int result = sum2(1,2,3,4,5); //그냥 리스트로 나열
int result=sum1(new int[] {1,2,3,4,5}); //배열을 줘도 됨
```

##### 추상 메소드

메소드의 선언부만 있고 실행내용이 없는 메소드. 자식 클래스는 **반드시** 추상 메소드를 오버라이딩 해서 실행 내용을 작성해야 한다. 

##### 리턴문

메소드 선언에 리턴 타입이 있다면 반드시 리턴문을 사용해야 한다. 리턴값이 없는 메소드에서 리턴문을 사용하면 메소드 실행을 강제 종료시킨다.

##### 오버로딩

매개값을 다양하게 받아 처리할 수 있도록 하기 위해서 오버로딩을 사용한다.

메소드 오버로딩은 매개변수의 타입, 개수, 순서 중 하나가 달라야 한다. 오버로딩된 메소드를 호출할 경우 JVM은 매개값의 타입을 보고 메소드를 선택한다. 

