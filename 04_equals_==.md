### 04) equals vs ==

공통적으로 둘다 모두 양 쪽에 있는 내용을 비교한 후에 boolean type으로 반환한다.

#### [ equals ]

`equals` 메소드는 자바 최상위 클래스인 `Object` 클래스에 정의되어있는 메소드입니다.

```java
boolean equals(Obejct obj)
```

`boolean equals(Object obj)`로 정의된 `equals `메소드는 2개의 객체가 동일한지 검사하기 위해 사용된다. 

기본적으로 eqauls가 구현된 방법은 2개의 객체가 참조하는 것이 동일한지를 확인하는 것이다.

즉, 2개의 객체가 가리키는 곳이 동일한 메모리 주소일 경우에만 동일한 객체가 된다.

하지만, `String` 클래스를 생각해보면 `equals` 메소드를 이용해 동일한 객체를 참조하는 것인지가 아니라, 안에 있는 문자열이 같은지 확인을 할 수 있다. 이처럼 우리가 사용하는 `String` 클래스 등은 `equals` 메소드를 오버라이딩해서 사용하고 있다.

`equals` 메소드는 `hashCode` 메소드를 이용해 비교를 진행하게 됩니다.

<br>

#### [ hashCode ]

`hashCode` 메소드는 `equals` 메소드와 마찬가지로 `Object` 클래스에 정의되어있는 메소드입니다.

```java
public native int hashCode();
```

기본적으로 heap에 저장된 객체의 메모리 주소를 반환하도록 되어있습니다.

<br>

#### [ equals와 hashCode의 관계 ]

동일한 객체는 동일한 메모리 주소를 갖는다는 것을 의미하므로, 동일한 객체는 동일한 해시코드를 가져야 한다. 그렇기 때문에 만약 우리가 equals() 메소드를 오버라이드 한다면, hashCode() 메소드도 오버라이드 되어야 한다.

이러한 equals와 hashCode의 관계를 정의하면 다음과 같다.

- Java 프로그램을 실행하는 동안 equals에 사용된 정보가 수정되지 않았다면, hashCode는 항상 동일한 정수값을 반환해야 한다. (Java의 프로그램을 실행할 때 마다 달라지는 것은 상관이 없다.)
- 두 객체가 equals()에 의해 동일하다면, 두 객체의 hashCode() 값도 일치해야 한다.
- 두 객체가 equals()에 의해 동일하지 않다면, 두 객체의 hashCode() 값은 일치하지 않아도 된다.

즉, obj1.equals(obj2) == True 이면 hashCode(obj1) == hashCode(obj2) 이여야하지만 hashCode(obj1) == hashCode(obj2) 라고 obj1.equals(obj2) == True일 필요는 없다.

하지만 우리는 다른 객체에 대해 동일한 hashCode를 생성한다면 hashTable을 생성하는데 불이익을 받을 수 있음을 인지하고 있어야 한다.

<br>

#### [ == ]

== 는 단순히 주소값을 비교하는 연산이다.

```java
String str1 = "aaa";
String str2 = new String("aaa");
System.out.println("str1 == str2 : " + (str1 == str2));
System.out.println("str1 equals str2 : " + (str1.equals(str2)));

// 출력
str1 == str2 : false
str1 equals str2 : true
```

==연산자와 String클래스의 equals()메소드의 가장 큰 차이점은 == 연산자는 비교하고자 하는 두개의 대상의 주소값을 비교하는데 반해 String클래스의 equals 메소드는 비교하고자 하는 두개의 대상의 값 자체를 비교합니다. 

일반적인 타입들 int형, char형등은 Call by Value 형태로 기본적으로 대상에 주소값을 가지지 않는 형태로 사용됩니다. 하지만 String은 일반적인 타입이 아니라 클래스입니다. 클래스는 기본적으로 Call by Reference형태로 생성 시 주소값이 부여됩니다. 그렇기에 String타입을 선언했을때는 같은 값을 부여하더라도 서로간의 주소값이 다를 수가 있습니다.