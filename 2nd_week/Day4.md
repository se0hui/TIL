# 형변환(다형성)

## 형변환

형변환과 형변환 연산자는 프로그래밍 중에 필수적인 요소다. 형변환을 통해 서로 다른 타입 간의 연산을 수행할 수 있고, 이를 통해 다형성을 구현할 수 있다.

형변환은 크게 묵시적 형변환과 명시적 형변환으로 나눌 수 있고, 기본형 변수화 참조 변수 모두에서 형변환을 사용할 수 있다.

<br>

## 기본형 변수의 형변환

**묵시적 형변환**: 컴파일러가 자동으로 수행하는 형변환이다. 작은 타입에서 큰 타입으로 변환할 때 발생하고, 데이터 손실이 없기 때문에 안전하다.

예시

```java
int i = 100;
long l = i; // 묵시적 형변환 (int -> long)
```

**명시적 형변환**: 개발자가 직접 형변환 연산자를 사용하여 수행하는 형변환이다. 큰 타입에서 작은 타입으로 변환할 때 사용되며, 데이터 손실이 발생할 수 있다.

예시

```java
long l = 100L;
int i = (int) l; // 명시적 형변환 (long -> int)
```

<br>

## 참조 변수의 형변환

참조 변수는 서로 상속 관계에 있는 클래스 사이에서 형변환이 가능하다. 부모 타입을 자식 타입으로, 자식 타입을 부모 타입으로 형변환할 수 있다.

**묵시적 형변환**: 자식 타입을 부모 타입으로 변환할 때 발생한다.

예시

```java
IPhone iPhone = new IPhone();
SmartPhone smartPhone = iPhone; // 묵시적 형변환 (IPhone -> SmartPhone)
```

**명시적 형변환**: 부모 타입을 자식 타입으로 변환할 때 발생하며, 반드시 형변환 연산자를 사용해야 한다.

예시

```java
SmartPhone smartPhone = new IPhone();
IPhone iPhone = (IPhone) smartPhone; // 명시적 형변환 (SmartPhone -> IPhone)
```

형변환이 불가능한 경우, 예외가 발생합니다.

```java
IPhone iPhone = new IPhone();
Galaxy galaxy = (Galaxy) iPhone; // 컴파일 에러
```

<br>

## Instanceof 연산자

참조 변수가 실제로 어떤 타입의 객체를 참조하고 있는지 확인하는 데 사용된다. 형변환이 가능한지 여부를 판단할 수 있다.

예시

```java
SmartPhone smartPhone = new IPhone();
if (smartPhone instanceof IPhone) {
    IPhone iPhone = (IPhone) smartPhone; // 안전한 명시적 형변환
}
```

<br>

## 다형성

객체 지향 프로그래밍의 중요한 개념 중 하나로, 하나의 요소가 여러 타입을 가질 수 있는 특성이다.
코드의 유연성, 재사용성을 높일 수 있다.
다형성은 주로 부모 클래스 타입의 참조 변수를 사용하여 자식 클래스의 인스턴스를 참조하는 방식으로 구현된다.

다형성의 장점:

- **유지보수 용이성**: 새로운 클래스가 추가되더라도 기존 코드를 수정할 필요가 적다.
- **코드 중복 감소**: 공통된 동작을 부모 클래스에 정의하여 코드 중복을 줄일 수 있다.

다형성의 예시:

스마트폰을 개통하는 프로그램을 다형성을 사용하여 구현하면, 새로운 스마트폰 클래스가 추가되더라도 쉽게 확장할 수 있다.

다형성 사용하지 않은 예:

```java
public class ActivateSmartPhone {
    void activateIPhone(IPhone iPhone, String model) {
        System.out.println(iPhone.getClass().getName() + " " + model + " 개통 완료");
    }

    void activateGalaxy(Galaxy galaxy, String model) {
        System.out.println(galaxy.getClass().getName() + " " + model + " 개통 완료");
    }

    public static void main(String[] args) {
        ActivateSmartPhone activateSmartPhone = new ActivateSmartPhone();
        activateSmartPhone.activateIPhone(new IPhone(), "13");
        activateSmartPhone.activateGalaxy(new Galaxy(), "S22");
    }
}
```

다형성을 사용한 예:

```java
public class ActivateSmartPhone {
    void activate(SmartPhone smartPhone, String model) {
        System.out.println(smartPhone.getClass().getName() + " " + model + " 개통 완료");
    }

    public static void main(String[] args) {
        ActivateSmartPhone activateSmartPhone = new ActivateSmartPhone();
        activateSmartPhone.activate(new IPhone(), "13");
        activateSmartPhone.activate(new Galaxy(), "S22");
    }
}
```

다형성을 활용하면 코드의 중복을 줄이고, 새로운 기능을 추가할 때에도 기존 코드를 수정할 필요 없이 확장할 수 있다.