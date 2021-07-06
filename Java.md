# Java

### 0) Java 언어 특징

자바는 썬 마이크로시스템즈의 제임스 고슬링이과 다른 연구원들이 개발한 객체 지향적 프로그래밍 언어이다. 자바 컴파일러는 자바 언어로 작성된 프로그램을 자바 바이트 코드라는 특수한 바이너리 형태로 변환하고 이를 JVM 이라는 특수한 가상 머신이 실행시키게 된다. 따라서, CPU나 운영 체제의 종류에 관계없이 JVM을 설치할 수 있는 시스템에서는 어디에서나 실행할 수 있으며 플랫폼 독립적이라는 큰 특징을 가진다.

#### 자바 언어의 5가지 철학

- 객체 지향 방법론을 사용해야 한다.
- 같은 프로그램(바이트코드)가 여러 운영체제에서 실행될 수 있어야 한다.
- 컴퓨터 네트워크 접근 기능이 기본으로 탑재되어있어야 한다.
- 원격 코드를 안전하게 실행할 수 있어야 한다.
- 다른 객체 지향 언어들의 장점만 가지고 와서 사용하기 편해야 한다.

<br>

### 1) Java 언어 플랫폼

자바 언어의 플랫폼은 4가지가 존재합니다.

- Java SE

  데스크톱 및 서버, 임베디드 시스템을 위한 표준 에디션의 자바 플랫폼

- Java EE

  서버측 개발을 위한 엔터프라이즈 에디션의 자바 플랫폼

  Java SE에 웹 애플리케이션 서버에서 동작하는 장애복구 및 분산 멀티티어를 제공하는 자바 소프트웨어의 기능을 추가

- Java ME

  마이크로 에디션의 자바 플랫폼

  제한된 자원을 가진 휴대 전화, PDA 세트톱박스 등에서 Java 언어를 지원하기 위해 만들어진 플랫폼

- Java FX

  데스크톱 애플리케이션과 리치 인터넷 애플리케이션(RIA)을 개발하고 배포하는 자바 플랫폼

--> Java SE 에서 구체적인 목적에 따라 API를 추가하거나 자바 가상 머신 규격 및 API의 일부를 택해서 다른 플랫폼들이 정의된다.

--> 우리가 흔히 자바 언어라고 하는 대부분의 패키지는 Java SE에 포함된 패키지를 의미!

<br>

### 2) JVM ( Java Virtual Machine )

<img src="https://user-images.githubusercontent.com/59816811/122666182-c738be00-d1e6-11eb-9e85-7de121cc3f18.png" alt="image" style="width:500px" />

1) 실행될 클래스 파일을 메모리에 로드 후 초기화 작업 수행

2) 메소드와 클랜스변수들을 해당 메모리 영역에 배치

3) 클래스로드가 끝난 후 JVM은 main 메소드를 찾아 지역변수, 객체변수, 참조변수를 스택에 쌓음

4) 다음 라인을 진행하면서 상황에 맞는 작업 수행

- Class Loader : JVM 내로 클래스를 로드하고 링크를 통해 배치하는 작업을 수행하는 모듈로써 런타임시 동적으로 클래스를 로드한다.
- Execution Engine : Class Loader를 통해 JVM 내의 런타임 데이터 영역에 배치된 바이트 코드를 실행한다. ( 자바 바이트 코드를 명령어 단위로 읽어서 실행한다. )
- Garbage Collector : JVM은 Garbage Collector를 통해 메모리 관리 기능을 자동으로 수행한다. 애플리케이션이 생성한 객체의 생존 여부를 판단하여 더 이상 사용되지 않는 객체를 해제하는 방식으로 메모리를 자동 관리한다.
- Runtime Data Area : JVM이 운영체제 위에서 실행되면서 할당받는 메모리 영역이다. Class Loader에서 준비한 데이터들을 보관하는 저장소이다.

<img src="https://user-images.githubusercontent.com/59816811/122667065-dec67580-d1eb-11eb-8e49-7d110e556dec.png" alt="image" style="width:500px;" />

- Method (Static) Area : JVM이 읽어들인 클래스와 인터페이스에 대한 런타임 상수 풀, 멤버 변수(필드), 클래스 변수(static 변수), 생성자와 메소드를 저장하는 공간이다.
- Runtime Constant Pool : 클래스와 인터페이스 상수, 메소드와 필드에 대한 모든 레퍼런스를 저장하고 있어 JVM은 런타임 상수 풀을 통해 메소드나 필드의 실제 메모리 상 주소를 찾아 참조한다.
- Heap Area : JVM이 관리하는 프로그램 상에서 데이터를 저장하기 위해 런타임 시 동적으로 할당하여 사용하는 영역이다. New 연산자로 생성된 객체들을 저장한다.
- Stack Area : 각 쓰레드마다 하나씩 존재하며, 쓰레드가 시작될 때 할당되는 영역이다. 메소드를 호출할 때마다 프레임을 추가하고 메소드가 종료되면 해당 프레임을 제거하는 동작을 수행한다. 기본타입 변수는 스택 영역에 직접 값을 가지고, 참조타입 변수는 힙 영역이나 메소드 영역의 객체 주소를 가지게 된다.
- PC Register : 현재 수행 중인 JVM 명령 주소를 가지고 있다. 연산 결과를 메모리에 전달하기 전에 저장하는 CPU 내의 기억 장치이다.
- Native Method Stack Area : 자바 외 언어로 작성된 네이티브 코드를 위한 Stack 영역이다.

OS 위에 존재하는 JVM 위에서 실행되기 때문에 운영체제에 독립적으로 실행될 수 있습니다. 하지만, JVM을 사용하기 때문에 많은 메모리를 사용하고 실행 속도가 느리다는 단점이 있습니다. 

실행하는 과정에서 JVM이 반드시 완벽하게 로딩되어야하기 때문에 프로그램의 초기 시작 시간이 C/C++에 비해 2~3배 정도 느리다고 알려져있습니다. 단적인 예로, 콘솔 화면에 달랑 "Hello, World"를 찍는 프로그램이 실행되는 데에도 AWT, Swing, SQL 같은 불필요한 기능까지 모두 로딩된 후에 실행되기 때문에 속도가 느릴 수 밖에 없습니다.

<br>

### 3) String vs StringBuildervs StringBuffer

자바에서 문자열을 다루는 객체는 크게 `String`, `StringBuffer`, `StringBuilder` 3개가 있습니다.

- String 객체
  - immutable 합니다. 즉, 한 번 생성이 되면 변경이 불가능 합니다.
  - 우리가 알고 있는 String 더하기 연산을 하여 2개의 String 객체를 붙일 시 새로운 객체가 생성되어 재할당되는 것입니다. 다라서, `Heap` 영역에 참조를 잃은 문자열 객체가 계속해서 쌓이게 되고, `GC`에 의해 수거가 되지만 메모리 관리 측면에서 좋지 않습니다. 
- StringBuilder
  - mutable 합니다. append() 메소드를 지원해서 문자열 값을 변경할 수 있습니다.
  - 멀티쓰레드 환경에서 동기화를 보장한다.
- StringBuffer
  - 멀티쓰레드 환경에서 동기화를 보장하는 StringBuilder

```java
String str1 = "hello";
String str2 = "world";
StringBuilder str3 = new StringBuilder("hello");
StringBuilder str4 = new StringBuilder("world");

System.out.println("str1.hashCode() = " + str1.hashCode());
System.out.println("str2.hashCode() = " + str2.hashCode());
System.out.println("str1 + str2 = " + (str1 + str2).hashCode()); // 새로운 객체 생성
System.out.println("str3.hashCode() = " + str3.hashCode());
System.out.println("str3 + str4 =  " + str3.append(str4).hashCode()); // str3 객체에 값이 변경

/*
str1.hashCode() = 99162322
str2.hashCode() = 113318802
str1 + str2 = -1524582912
str3.hashCode() = 391447681
str4.hashCode() = 1935637221
str3 + str4 =  391447681 
*/
```

