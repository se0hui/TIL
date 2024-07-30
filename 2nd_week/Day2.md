# 접근제어자, static, get, set, 캡슐화

## 접근제어자

클래스의 멤버(필드, 메서드)에 대한 접근 권한을 제어하는 키워드다.

주요 접근 제어자:

- public: 모든 클래스에서 접근할 수 있음
- protected : 같은 패키지 내의 클래스 및 서브 클래스에서 접근할 수 있음
- private : 같은 클래스 내에서만 접근할 수 있음
- default : 접근 제어자가 선언되지 않은 경우, 같은 패키지 내의 클래스에서만 접근할 수 있음

```java
public class Ex {
    public int publicField;
    protected int protectedField;
    private int privateField;
    int packagePrivateField;
}
```

<br>

## static

static 키워드는 클래스의 멤버가 클래스 자체에 속하는 데 사용된다. 인스턴스에 속하지 않고, 클래스 로딩 시점에 초기화 된다.

- 정적 필드 : 모든 인스턴스가 공유하는 변수
- 정적 메서드 : 인스턴스를 생성하지 않고 클래스 이름으로 직접 호출할 수 있는 메서드

```java
public class Ex {
    public static int staticField;

    public static void staticMethod() {
        System.out.println("Static method called");
    }
}
```

<br>

## get & set

get과 set 메서드는 클래스의 private 필드에 접근하고, 값을 설정하거나 가져오기 위해 사용된다. 이를 통해 필드에 대한 직접 접근을 막고, 필요한 경우 값의 유효성을 검사할 수 있다.

<br>

### get 메서드

- 역할: 필드의 값을 반환한다.
- 이름 규칙: 일반적으로 get으로 시작하고, 뒤에 필드명을 붙인다.

```java
public double getBalance() {
    return balance;
}
```

<br>

### set 메서드

- 역할: 필드의 값을 설정한다.
- 이름 규칠: 일반적으로 set으로 시작하고, 뒤에 필드명을 붙인다.

```java
public void setBalance(double balance) {
    if (balance >= 0) {
        this.balance = balance;
    }
}
```

<br>

```java
public class Person {
    private String name;
    private int age;

    // name 필드의 getter 메서드
    public String getName() {
        return name;
    }

    // name 필드의 setter 메서드
    public void setName(String name) {
        if (name != null && !name.trim().isEmpty()) {
            this.name = name;
        }
    }

    // age 필드의 getter 메서드
    public int getAge() {
        return age;
    }

    // age 필드의 setter 메서드
    public void setAge(int age) {
        if (age > 0) {
            this.age = age;
        }
    }
}
```

<br>

## 캡슐화

데이터와 메서드를 하나의 단위로 묶는 것.
데이터를 외부로부터 보호하고, 데이터를 다루는 메서드를 통해 접근하도록 한다.

- 목적:
  - 데이터의 무결성 유지
  - 시스템 복잡성 감소
  - 유지보수성 향상

- 장점
  - 데이터 보호: 필드를 private로 선언하고, 외부에서 직접 접근하지 못하도록 한다.
  - 데이터 무결성: set 메서드를 통해 값의 유효성을 검사하고, 잘못된 데이터가 설정되는 것을 방지할 수 있다.
  - 모듈화: 클래스 내부의 구현을 숨기고, 필요한 인터페이스만 외부에 제공하며 코드를 모듈화할 수 있다.
  - 유지보수성: 캡슐화를 통해 코드 변경이 발생해도 외부에 미치는 영향을 최소화할 수 있다.

```java
public class Student {
    // 필드는 private으로 선언하여 외부에서 직접 접근하지 못하도록 합니다.
    private String name;
    private int age;

    // name 필드의 getter 메서드
    public String getName() {
        return name;
    }

    // name 필드의 setter 메서드
    public void setName(String name) {
        // 유효성 검사: 이름이 null이 아니고 빈 문자열이 아닌 경우에만 설정합니다.
        if (name != null && !name.trim().isEmpty()) {
            this.name = name;
        } else {
            System.out.println("Invalid name");
        }
    }

    // age 필드의 getter 메서드
    public int getAge() {
        return age;
    }

    // age 필드의 setter 메서드
    public void setAge(int age) {
        // 유효성 검사: 나이가 0보다 큰 경우에만 설정합니다.
        if (age > 0) {
            this.age = age;
        } else {
            System.out.println("Invalid age");
        }
    }
}
```
