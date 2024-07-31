# 상속, 오버라이딩, 오버로딩

## 상속

정의: 부모 클래스의 속성과 메서드를 자식 클래스가 물려받는 것
목적: 모드의 재사용성 증대, 코드 중복 감소, 유지보수 용이성, 확장성 강화.

특징:

- 단일 상속: Java는 클래스의 단일 상속만 지원한다.
- extends 키워드: 상속을 구현할 때 사용한다.
- 접근 제한자: private멤버는 상속되지 않으며, default 접근자는 같은 패키지 내에서만 상속이 가능하다.


인터페이스와 상속:

- implements 키워드: 인터페이스 구현 시 사용한다.
- 다중 사옥 가능: 인터페이스는 다중 상속이 가능하다.
- 오버라이딩: 인터페이스의 모든 메서드는 반드시 구현해야 한다.

```java
// 부모 클래스
public class Animal {
    public void eat() {
        System.out.println("This animal eats food.");
    }
}

// 자식 클래스
public class Dog extends Animal {
    public void bark() {
        System.out.println("The dog barks.");
    }
}

public class Main {
    public static void main(String[] args) {
        Dog myDog = new Dog();
        myDog.eat();  // 부모 클래스의 메서드 사용
        myDog.bark(); // 자식 클래스의 메서드 사용
    }
}
```

<br>

## 오버라이딩

개념: 상위 클래스의 메서드를 하위 클래스에서 재정의
특징:

- 메서드 이름, 매개변수, 반환형이 같아야 한다.
- 접근 제어자는 부모 클래스보다 좁게 설정할 수 없다.
- 예외는 부모 클래스보다 많이 선언할 수 없다.
- static 메서드는 오버라이딩이 불가능하다.

```java
// 부모 클래스
public class Animal {
    public void preference() {
        System.out.println("동물을 좋아한다.");
    }
}

// 자식 클래스
public class Cat extends Animal {
    @Override
    public void preference() {
        System.out.println("고양이를 좋아한다.");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal myAnimal = new Animal();
        myAnimal.preference();  // 출력: 동물을 좋아한다.

        Cat myCat = new Cat();
        myCat.preference();     // 출력: 고양이를 좋아한다.
    }
}
```

<br>

## 오버로딩

개념: 같은 이름의 메서드를 여러 개 정의, 매개변수의 유형이나 개수가 다름
특징:

- 리턴 타입만 다른 메서드는 혀용되지 않는다.
- 같은 기능을 하는 메서드를 하나의 이름으로 사용하여 메서드 이름을 절약한다.

```java
public class MathUtils {
    // 두 정수를 더하는 메서드
    public int add(int a, int b) {
        return a + b;
    }

    // 세 정수를 더하는 메서드
    public int add(int a, int b, int c) {
        return a + b + c;
    }

    // 두 실수를 더하는 메서드
    public double add(double a, double b) {
        return a + b;
    }
}

public class Main {
    public static void main(String[] args) {
        MathUtils utils = new MathUtils();
        System.out.println(utils.add(2, 3));          // 출력: 5
        System.out.println(utils.add(2, 3, 4));       // 출력: 9
        System.out.println(utils.add(2.5, 3.5));      // 출력: 6.0
    }
}
```
