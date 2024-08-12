# 접근제어자, static, get, set, 캡슐화

## 접근제어자

클래스의 멤버(필드, 메서드)에 대한 접근 권한을 제어하는 키워드다.

주요 접근 제어자:

| 접근자 | 클래스 내부 |패키지 | 상속받은 클래스 | 이외의 영역 |
| ------ | ------ | ------ | ------ | ------|
|private|O|X|X|X|
|defualt|O|O|X|X|
|protected|O|O|O|X|
|public|O|O|O|O|

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

**접근 제어자를 사용하는 이유**

 - 보안: 객체 내부의 데이터와 메소드를 보호하여 잘못된 접근으로 인한 문제를 방지한다
 - 정보 은닉: 객체의 내부 구조를 숨기고, 필요한 인터페이스만 외부에 제공한다. 의도하지 않은 코드 사용을 줄이고, 코드의 유지보수를 용이하게 한다.

<br>

## static

정의:static은 클래스에 속하는 요소를 정의, 인스턴스와 관계없이 공유되는 값을 갖는다.

특징:

- 변수: static 변수는 클래스가 로드될 때 메모리에 할당된다. 모든 인스턴스가 동일한 값을 공유한다.
- 메서드: static메서드는 인스턴스 없이 호출 가능, 인스턴스 멤버에 직접 접근할 수 없다.

static의 단점:

- 객체와 다른 라이프사이클: static 변수는 클래스가 로드될 때 메모리에 할당되며, 클래스가 종료되어도 메모리에서 회수되지 않는다.
- 메모리 문제: static 변수는 프로그램 전체에서 공유되기 때문에 많은 호출로 메모리 문제를 일으킬 수 있다.
- 상호 의존성: 모든 스레드에서 static 필드를 공유하여 스레드 간 상호작용 문제가 발생할 수 있다.
- 오버라이딩 불가: static 메서드는 오버라이딩할 수 없어 클래스 확장이 어렵다.

static 메모리와 속도 측면에서 유리할 수 있지만, 객체지향 프로그래밍에서는 객체의 캡슐화를 위해 지양하는 것이 좋다.

<br>

## get & set

목적: 객체의 필드를 외부에서 안전하게 접근하고 변경할 수 있도록 하는 메서드

캡슐화: 객체의 필드를 private으로 설정하고, 필드에 접근할 수 있는 메소드를 통해서만 접근하도록 유도하여 데이터 무결성을 유지한다.

<br>

### get 메서드

- 역할: 필드의 값을 반환한다.
- 이름 규칙: 일반적으로 get으로 시작하고, 뒤에 필드명을 붙인다.
- boolean 필드: 메소드 이름은 'is+필드 이름'으로 한다.

```java
public 타입 getFieldName() {
    return fieldName;
}
```

<br>

### set 메서드

- 역할: 필드의 값을 설정한다.
- 이름 규칙: 일반적으로 set으로 시작하고, 뒤에 필드명을 붙인다.
- 매개 변수: 필드 타입과 동일해야한다.

```java
public void setFieldName(타입 fieldName) {
    this.fieldName = fieldName;
}
```

<br>

예제

```java
public class Car {
    private int speed;
    private boolean stop;

    // Getter
    public int getSpeed() {
        return speed;
    }

    public boolean isStop() {
        return stop;
    }

    // Setter
    public void setSpeed(int speed) {
        if(speed < 0) {
            this.speed = 0;
        } else {
            this.speed = speed;
        }
    }

    public void setStop(boolean stop) {
        this.stop = stop;
        this.speed = 0;
    }
}

public class CarExample {
    public static void main(String[] args) {
        Car myCar = new Car();   // 객체 생성

        // 잘못된 속도 변경
        myCar.setSpeed(-50);
        System.out.println("현재 속도 : " + myCar.getSpeed());  // 0 출력

        // 올바른 속도 변경
        myCar.setSpeed(60);

        // 멈춤
        if(!myCar.isStop()) {
            myCar.setStop(true);
        }

        System.out.println("현재 속도 : " + myCar.getSpeed());  // 0 출력
    }
}
```

<br>

## 캡슐화

데이터를 메서드와 함께 하나의 단위로 묶고, 데이터를 외부로부터 보호하는 기법이다. 데이터의 직접 접근을 제한하고, 데이터를 다루는 메서드를 통해 접근하도록 한다.

- 목적:
  - 데이터의 무결성 유지
  - 시스템 복잡성 감소
  - 유지보수성 향상

- 장점
  - **데이터 보호**: 필드를 private로 선언하고, 외부에서 직접 접근하지 못하도록 한다.
  - **데이터 무결성**: set 메서드를 통해 값의 유효성을 검사하고, 잘못된 데이터가 설정되는 것을 방지할 수 있다.
  - **모듈화**: 클래스 내부의 구현을 숨기고, 필요한 인터페이스만 외부에 제공하며 코드를 모듈화할 수 있다.
  - **유지보수성**: 캡슐화를 통해 코드 변경이 발생해도 외부에 미치는 영향을 최소화할 수 있다.

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
