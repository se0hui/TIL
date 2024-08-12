# Bean / Component

## Bean

@Bean은 메서드 수준에서 사용되는 어노테이션이고, 개발자가 직접 빈을 생성하고 설정할 수 있다.

주로 @Configuration 클래스 내에서 사용되고, 복잡한 초기화나 외부 라이브러리의 클래스를 빈으로 등록할 때 유용하다.

'@Bean'을 사용하면 개발자가 빈의 생성 과정을 더 세밀하게 관리할 수 있다.

<br>

```java
@Configuration
public class MyConfig {

    @Bean
    public MyService myService() {
        return new MyService();
    }
}
```

<br>

## Component

클래스의 수준에서 사용되는 어노테이션이다.
@Component는 해당 클래스를 스프링의 빈으로 등록한다.

@Component는 자동으로 스캔되어 빈으로 등록되고, 스프링의 의존성 주입 기능을 통해 다른 객체에 주입될 수 있다.

주로 간단하게 클래스를 빈으로 생성하고자 할 때 사용된다.

<br>

```java
@Component
public class MyComponent {
    public void doSomething() { }
}
```

<br>

## Bean과 Component의 차이점

| 헤더 | @Component | @Bean |
|------|-------|-------|
| 어디에 사용되는가? | 자바 클래스에 사용 | 빈에 등록시킬 클래스를 생성하는 함수에 사용되고, 특히 Spring Configuration에서 클래스 생성 함수에 사용된다.|
|사용 난이도| 매우 쉬움(붙이기만 하면 됨)| 상대적으로 어렵다(직접 하나씩 붙여야 한다. 생성 로직을 작성해야 한다.)|
|Autowiring| @Autowired로 필드에 직접, 세터, 생성자로 주입이 가능하다.|클래스를 생성할 때 Bean에 등록 시키고자 하는 클래스를 직접 생성하거나 파라미터로 받는다.|
|누가 만드는 가| Spring Framework | 생성자 빈을 직접 정의해야 한다.|
|언제 사용하는게 좋은가? | 직접 작성한 클래스를 빈에 등록시키려 할 때| 1. 의존성을 주입할 때 특정 로직을 실행시켜주고 싶을때. 2. 내가 만든게 아닌 다른 사람의 로직을 사용할 때|
