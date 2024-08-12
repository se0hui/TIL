# 어노테이션

## 어노테이션이란?

사전적 의미: **주석**

자바에서 어노테이션은 코드 사이에 특별한 의미, 기능을 수행하도록 하는 기술이다.

**역할**:

- 컴파일러에게 문법 에러를 체크하도록 정보 제공
- 프로그램을 빌드할 때 코드를 자동으로 생성할 수 있도록 정보 제공
- 런타임에 특정 기능을 실행하도록 정보를 제공

어노테이션은 @를 사용하여 작성하고, 해당 타겟에 대한 동작을 수행하는 프로그램 외에는 다른 프로그램에게 영향을 주지 않는다.

**어노테이션을 사용하기 위한 순서**:

1. 어노테이션을 정의한다.
2. 클래스에 어노테이션을 배치한다.
3. 코드가 실행되는 중에 Reflection을 이용하여 추가 정보를 획득하여 기능을 실시한다

<br>

## 어노테이션의 종류

### 표준 어노테이션

: 자바에서 기본적으로 제공하는 어노테이션

---

#### @Override

컴파일러에게 메서드를 **오버라이딩**하는 것이라고 알린다.

```java
@Override
public String toString(){
    return "Test";
}
```

#### @Deprecated

앞으로 **사용하지 않을 대상**임을 알린다.

```java
@Deprecated
public void oldMethod(){
    System.out.println("This method is deprecated.");
}
```

#### @Functionallnterface

**함수형 인터페이스**라는 것을 알린다.

> 함수형 인터페이스: 단 하나의 추상 메서드를 가지는 인터페이스

```java
@Functionallnterface
public interface exampleInterface{
    public abstract void example();
}
```

#### @SuppressWarning

컴파일러가 **경고 메시지를 나타내지 않는다**.

```java
@SuppressWarning("unused")
public void suppressedWarningMethod(){
    int unusedVariable = 42;
}
```

### 메타 어노테이션

어노테이션에 붙이는 어노테이션으로, 어노테이션을 정의하는 데 사용한다.

---

#### @Target

어노테이션을 정의할 때 **적용 대상을 지정**하는 데 사용한다.

```java
@Target(ElementType.FIELD)
public @interface MyFieldAnnotation{ }
```

#### @Documented

어노테이션 정보를 **javadoc으로 작성된 문서에 포함** 시킨다.

```java
@Documented
public @interface CustomAnnotation{ }
```

#### @Inherited

어노테이션이 **하위 클래스에 상속**되도록 한다.

```java
@Inherited
@interface SuperAnnotation{ }

@SuperAnnotation
class Super { }

class Sub extends Super{ } // 상위 클래스와 Super와 동일하게 @SuperAnnotation에 정의된 내용들을 적용받는다.
```

#### @Retention

어노테이션이 **유지되는 기간**을 정하기 위해 사용한다.

```java
@Retention(RetentionPolicy.RUNTIME)
public @interface MyRuntimeAnnotation{ }
```

#### @Repeatable

어노테이션을 **반복해서 적용**할 수 있도록 한다.

```java
@Repeatable(Work.class)
@interface Work{
    String value();
}

@Work("code update")
@Work("method overriding")
class Main{
    ...
}
```

### Spring 어노테이션

#### @Bean

메서드에 붙여서 해당 메서드의 반환값을 Bean으로 등록한다.

```java
@Bean
public MyService myService(){
        return new MyServiceImpl();
    }
```

#### @Configuration

클래스를 Spring의 구성 클래스로 지정하여, 그 안의 @Bean 메서드들로 Bean을 정의하고 관리한다.

```java
@Configuration
public class AppConfig{

    @Bean
    public MyService myService(){
        return new MyServiceImpl();
    }
    
    @Bean
    public MyRepository myRepository(){
        return new MyRepositoryImpl();
    }
}
```

#### @Component

자동으로 Bean을 생성하고 관리하기 위해 사용한다.

```java
@Component
public class MyComponent{
    public void printHello(){
        Systme.out.println("Hello!");
    }
}
```

#### @Import

다른 구성 클래스를 현재 구성 클래스에 추가하여 여러 구성 클래스를 통합하는데 사용한다.

```java
@Configuration
@Import(AdditionalConfig.class)
public class MainConfig{ }
```

#### @Service

비즈니스 로직을 수행하는 서비스 컴포넌트를 정의하고 관리하는데 사용된다.

```java
@Service
public class UserService {
    public void performService() {
        System.out.println("User service is being performed.");
    }
}
```

#### @Autowired

자동으로 의존성을 주입하여 필요한 Bean을 주입받도록 설정한다.

```java
@controller
public class MainController{
    @autowied
    Member member1;
}
```

#### @Primary

여러 개의 Bean이 동일한 타입을 제공할 때, 기본적으로 사용할 Bean을 지정하는데 사용한다.

```java
@Configuration
public class AppConfig{

    @Bean
    @Primary
    public MyService primaryService(){
        return new PrimaryMyService();
    }
    
    @Bean
    public MyService secondaryService(){
        return new SecondaryMyServiceImpl();
    }
}
```

#### @Value

외부 설정 값을 Bean의 필드나 메서드에 주입하는 데 사용된다.

```java
@Component
public class MessageService{
    @Value("${greeting.message}")
    private String message;
}
```

#### @Lazy

Bean을 초기화할 때 지연 로딩을 적용하여, Bean이 필요할 때까지 생성하지 않도록 한다.

```java
@Lazy
@Component
public class LazyService {
    public LazyService() {
        System.out.println("LazyService bean is being created!");
    }
}
```

#### @Scope

Bean의 생명주기와 범위를 정의하여 Bean의 인스턴스 생ㅁ=성 및 관리 방식을 설정한다.

```java

@Component
@Scope("prototype") //ProtoType 스코프는 요청할 때마다 새로운 Bean 인스턴스를 생성한다.
public class PrototypeService {
    public void showMessage() {
        System.out.println("Hello from PrototypeService!");
    }
}
```

#### @Profile

특정 환경에서만 Bean을 활성화, 또는 비활성화하여 다양한 설정을 프로파일별로 관리할 수 있도록 도와준다.

```java
@Component
@Profile("prod")  // 'prod' 프로파일이 활성화된 경우에만 Bean으로 등록됩니다.
public class ProdService {
    public void performProdTask() {
        System.out.println("Prod profile active");
    }
}
```

#### @Controller

Spring MVC에서 웹 요청을 처리하는 컨트롤러 클래스를 정의하고, HTTP 요청을 수신 및 응답을 반환하는 역할을 한다.

```java
@Controller
public class TestController {

    @GetMapping("/test")
    public String test(){
        return "test!";
    }
}
```

#### @RestController

Spring MVC에서 RESTful 웹 서비스를 위한 컨트롤러 클래스를 정의하고, HTTP 요청 처리 및 JSON 또는 XML 형식으로 응답을 반환한다.

```java
@RestController
public class TestController {

    @GetMapping("/api/test")
    public String test(){
        return "test!";
    }
}
```

#### @RequestMapping

HTTP 요청을 특정 메서드와 매핑하여 URL 경로와 HTTP 메서드에 따라 컨트롤러 메서드를 호출한다.

```java
@RestController
@RequestMapping("/api")
public class TestController {

    @GetMapping("/test")
    public String test(){
        return "test!";
    }
}
```

#### @RequestParam

HTTP 요청 파라미터를 메서드 파라미터로 바인딩하여 컨트롤러 메서드에서 사용할 수 있도록 한다.

```java
@RestController
@RequestMapping("/api")
public class HelloController {

    @GetMapping("/hello")
    public String hello(@RequestParam(name = "name", defaultValue = "Guest") String name) {
        return "Hello," + name + "!";
    }
}
```

#### @PathVariable

URL 경로의 변수 값을 메서드 파라미터로 바인딩하여 컨트롤러 메서드에서 사용할 수 있도록 한다

```java
@RestController
@RequestMapping("/api")
public class UserController {

    @GetMapping("/user/{userId}")
    public String getUser(@PathVariable("userId") String userId) {
        return userId;
    }
}
```
