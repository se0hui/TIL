# Spring DI / IoC

## 스프링의 콘셉트

---

- **IoC: 제어의 역전**: 객체의 생성 및 제어를 개발자가 아닌 스프링 컨테이너가 관리한다.
- **DI: 의존성 주입**: 객체 간의 의존성을 외부에서 주입받아 결합도를 낮추고 유연성을 높인다.
- AOP: 관점 지향 프로그래밍
- PSA: 이식 가능한 서비스 추상화

<br>

### IoC(Inversion of Control)

---

IoC는 객체의 생성과 제어를 스프링 컨테이너가 담당하는 것을 의미한다.
개발자는 객체를 직접 생성하지 않고, **필요한 객첼르 외부에서 받아 사용한다**

<br>

- 클래스 A에서 클래스 B 객체 생성 예

```java
public class A{
    b = new B();
}
```

<br>

- 제어의 역전을 적용한 예

```java
public class A{
    private B b;
}
```

<br>

제어의 역전을 적용하면 객체를 외부에서 관리하게 되고, 실제로 사용할 때에는 **외부**에서 제공해주는 객체를 받아오게 된다.
> **외부** -> 스프링 컨테이너:
> 객체를 관리하는 주체

<br><br>

## DI(Dependency Injection)

---

DI는 IoC를 구현하기 위한 방법으로, **클래스가 필요한 의존 객체를 외부에서 주입**받는다.

이를 통해 **모듈 간의 결합도가 낮아지고 유연성이 높아진다**.

<br>

- 스프링은 이용한 DI 코드 예

```java
public class A{
    //A에서 B를 주입받음
    @Autowired
    B b;
}
```

- '**@Autowired**' 어노테이션은 스프링 컨테이너에서 B 객체를 주입받는다. 개발자는 직접 객체를 생성하지 않고 스프링이 관리하는 객체를 사용하게 된다
    >Bean: 스프링 컨테이너에서 관리하는 객체

DI의 장점

- **유연성 증가**: 객체 간의 결합도가 낮아져서 코드 변경이 용이
- **테스트 용이성**: 의존성 주입을 통해 테스트하기 쉬운 구조로 변경
- **코드 재사용성**: 객체를 재사용할 수 있어 유지보수성이 높아짐

<br>

### DI 종류

- **필드 주입**: 객채의 필드에 직접 주입하는 방식

```java
public class A{
    //A에서 B를 주입받음
    @Autowired
    B b;
}
```

- **생성자 주입**: 생성자를 통해 객체를 주입하는 방식

```java
public class A {
    private B b;

    @Autowired
    public A(B b) {
        this.b = b;
    }
}
```

- **세터 주입**

```java
public class A {
    private B b;

    @Autowired
    public void setB(B b) {
        this.b = b;
    }
}
```

- **어노테이션**
  - **'@Autowired'**: 스프링 컨테이너에서 빈을 주입받을 때 사용
  - **'@Component'**: 클래스가 빈으로 등록됨을 나타냄
  - **'@Service', '@Repository', '@Controller'**: 각각 서비스, 리포지토리, 컨트롤러 역할을 하는 빈을 등록할 때 사용

<br>

![image.png](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FsLqxZ%2FbtshAuR8Dz3%2FIBLqK6YUkJkX3OPTRxmwR1%2Fimg.png)

> 스프링 컨테이너가 B 객체를 만들어 주입

<br><br><br>

-----

### <span style = "color : gray"> Bean</span>

스프링 컨테이너가 생성가호 관리하는 객체

빈을 스프링 컨테이너에 등록하기 위해 XML 파일에서 설정하거나, 어노테이션으로 등록하는 등의 방법을 제공한다.

>클래스를 빈으로 등록하는 방법 예

```java
@Component // 클래스 MyBean을 빈으로 등록
public class MyBean{ }
```

<br><br>

### <span style = "color : gray"> 스프링 컨테이너 </span>

스프링 컨테이너는 빈을 관리하며, 애플리케이션 실행 시 빈을 생성하고 주입한다. 이를 통해 객체 간의 의존성을 관리하고 애플리케이션의 라이프 사이클을 제어한다.