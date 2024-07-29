# 클래스, 메소드, 필드, 객체, 인스턴스

## 클래스
클래스는 객체를 정의하는 템플릿 또는 청사진이다. 클래스는 객체의 속성(필드)과 동작(메소드)을 정의한다.

## 메소드
메소드는 클래스에서 정의된 함수이다. 메소드는 객체의 동작이나 행동을 정의한다. 메소드는 클래스 내에서 정의되고, 객체가 할 수 있는 작업을 나타낸다.

## 필드
필드는 클래스에서 정의된 데이터 멤버이다. 필드는 객체가 가질 수 있는 상태나 속성을 나타낸다. 필드는 인스턴스 변수(각 객체마다 독립적으로 존재) 또는 클래스 변수(모든 객체가 공유)일 수 있다.

- **인스턴스 변수**: 각 객체마다 독립적으로 존재하며, 객체가 생성될 때 초기화된다. 예를 들어, 자동차의 색상이나 모델이 인스턴스 변수일 수 있다.
- **클래스 변수**: 모든 객체가 공유하는 변수로, 클래스 자체에 속한다. 예를 들어, 모든 자동차 객체가 공유하는 생산 공장 위치가 클래스 변수가 될 수 있다.

## 객체
객체는 클래스로부터 생성된 구체적인 실체이다. 객체는 클래스에서 정의된 속성과 행동을 가진다.

## 인스턴스
인스턴스는 객체의 구체적인 예이다. 인스턴스는 클래스의 템플릿을 바탕으로 생성된 객체를 의미한다. 클래스가 자동차의 설계도라면, 인스턴스는 실제로 만들어진 개별 자동차다. 인스턴스와 객체는 거의 같은 의미로 사용되지만, 인스턴스는 객체가 특정 클래스의 예임을 강조할 때 사용된다.

## 연관 관계
- **클래스와 객체/인스턴스**: 클래스는 객체를 생성하기 위한 템플릿이다. 객체는 클래스의 인스턴스다. 예를 들어, '자동차' 클래스에서 여러 객체(예: 내 자동차, 네 자동차)가 생성될 수 있다.
- **클래스와 필드**: 클래스는 필드를 정의한다. 필드는 클래스의 속성을 나타낸다. 각 객체는 이 필드의 값을 가질 수 있다.
- **클래스와 메소드**: 클래스는 메소드를 정의한다. 메소드는 클래스의 행동을 나타낸다. 각 객체는 이 메소드를 사용할 수 있다.
- **객체와 필드**: 객체는 클래스의 필드를 자신의 속성으로 가진다. 각 객체는 클래스의 필드에 대한 고유한 값을 가질 수 있다.
- **객체와 메소드**: 객체는 클래스의 메소드를 호출할 수 있다. 객체는 이 메소드를 사용하여 특정 행동을 수행한다.

### 예시
```java
public class Car {
    public static String factoryLocation = "Seoul";  // 클래스 변수

    private String color;  // 인스턴스 변수
    private String model;  // 인스턴스 변수

    public Car(String color, String model) {
        this.color = color;
        this.model = model;
    }

    public void drive() {
        System.out.println("The " + color + " " + model + " is driving.");
    }

    public void stop() {
        System.out.println("The " + color + " " + model + " has stopped.");
    }

    public String getColor() {
        return color;
    }

    public String getModel() {
        return model;
    }

    public static void main(String[] args) {
        // 클래스 Car의 인스턴스(객체) 생성
        Car myCar = new Car("red", "Toyota");
        Car yourCar = new Car("blue", "Honda");

        // 객체의 필드 접근
        System.out.println(myCar.getColor());  // 출력: red
        System.out.println(yourCar.getModel());  // 출력: Honda

        // 클래스 변수 접근
        System.out.println(Car.factoryLocation);  // 출력: Seoul

        // 객체의 메소드 호출
        myCar.drive();  // 출력: The red Toyota is driving.
        yourCar.stop();  // 출력: The blue Honda has stopped.
    }
}
```

- 클래스 : 'Car'
- 필드 : 'color', 'model'
- 메소드 : 'drive', 'stop'
- 'Car' 클래스의 객체 : ''my_car', 'your_car'
  - 각 객체는 클래스의 인스턴스