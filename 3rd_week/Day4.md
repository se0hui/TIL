# DAO DTO VO / Builder Pattern

## DAO, DTO, VO

### DAO (Data Access Object)

: 실제로 DB의 데이터에 접근하는 객체

---

데이터 베이스와 상호작용하는 객체

DB에 접근하기 위한 로직을 분리하기 위해 사용한다. 직접 DB에 접근하여 data를 삽입, 삭제, 조회 등 CRUD 기능을 수행한다.

로직을 분리하여 코드의 가독성을 높이고 유지보수를 쉽게 한다.

> JPA에서는  'JpaRepository'를 상속받는 Repository 객체가 DAO 역할을 한다

```java
public interface BoardRepo extends JpaRepository<Board, Long> {
}
```

<br>

### DTO (Data Transfer Object)

:계층 간(Controller, View, Business Layer) 데이터 교환을 위한 객체

---

계층 간에 데이터를 전달하기 위한 객체

데이터만 담고 있으며, 데이터에 대한 로직은 없다.

DB에서 데이터를 읽어와서 Service나 Controller 등으로 보낼 때 사용한다.

단순히 데이터의 저장과 전달만을 목적으로 한다.

- 예시

```java
@Getter
@Setter
public class BoardDTO{
    private Long id;
    private String title;
    private String content;
    private String writer;
}
```

<br>

### VO (Value Object)

: Read-Only(변경 불가능하며 읽기만 가능) 속성을 가진 값 오브젝트

---

데이터 자체에 의미를 부여하는 객체이다.

데이터를 수정할 수 없기 때문에 불변성을 가진다.

DTO는 setter를 가지고 있어 값을 변경할 수 있지만, VO는 getter만을 가지기 때문에 읽기만 가능하고 수정은 불가능하다.

<br><br>

#### DTO와 VO의 차이점

DTO는 인스턴스 개념이고, VO는 리터럴 값(변하지 않는 데이터) 개념이다.

<br>

DTO는 단지 데이터를 담아 전달하는 역할만 하지만, VO는 Read-Only 속성을 가져 객체로서 데이터 그 자체에 의미를 갖는다.

<br><br>

## Builder Pattern

: 복잡한 객체 생성 과정을 단순화하고, 생성 과정과 표현 방법을 분리하여 다양한 객체를 유연하게 생성할 수 있게 해주는 디자인 패턴

---

### 생성 패턴

빌터 패턴은 생성 패턴 중 하나이며 생성 패턴은 인스턴스를 만드는 절차를 추상화하는 패턴이다.

생성 패턴은 객체를 생성, 합성하는 방법이나 객체의 표현 방법을 시스템과 분리해준다.

생성 패턴을 이용하면 무엇이 생성되고, 누가 이것을 생성하며, 어떻게 생성되는지, 언제 생성할 것인지 결정하는 데 유연성을 확보할 수 있다.

### 빌더 패턴의 장점

- 클라이언트 코드의 가독성을 높인다.
- 불필요한 매개변수 전달을 피한다.
- 객체의 일관성과 안정성을 보장한다.
- 디폴트 매개변수 생략을 간접적으로 지원하며, 필수 멤버와 선택적 멤버를 분리할 수 있다.

### 빌더 패턴의 구현 방법

- **빌더 클래스 정의:**
  - 생성할 클래스(ex. 'Computer')의 내부에 'Static Nested Class'로 빌더 클래스를 만든다.
  - 클래스 이름에 'Builder'를 붙여 'ComputerBuilder'로 정의한다.
- **생성자 정의:**
  - 빌더 클래스의 생성자는 'public'으로 하고, 필수 값들을 매개변수로 받는다.
- **옵셔널 값 설정:**
  - 각 속성마다 메서드를 제공하며, 메서드의 반환값은 빌더 객체 자신이다.
- **build() 메서드 정의:**
  - 빌더 클래스 내에 'build()' 메서드를 만들어 최종 객체를 반환한다.
  - 생성 대상 클래스의 생성자는 'private'로 정의한다.
<<<<<<< HEAD
  
=======
>>>>>>> a027128d77f51670b0fb266110d9fd8129f43c00
