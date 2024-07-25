# **<span style = "color : purple">객체 지향 설계의 5가지 원칙</span>**

## SOLID 원칙?
---

**SOLID 원칙**은 <span style = "color : #9999FF">객체 지향 설계에서 지켜줘야 할 5개의 소프트웨어 개발 원칙</span>을 말한다.
5가지 원칙들은 서로 개념적으로 연관되어 있다. 시스템의 변경에 유연하게 대응할 수 있는 구조를 설계하는 데 도움을 준다.

1. **<span style = "color:violet">S</span>RP(Single Responsibility Principle)** : 단일 책임 원칙

2. **<span style = "color:violet">O</span>CP(Open Closed Priciple)** 개방 폐쇄 원칙

3. **<span style = "color:violet">L</span>SP(Listov Substitution Principle)** : 리스코프 치환 원칙

4. **<span style = "color:violet">I</span>SP(Interface Segregation Principle)** : 인터페이스 분리 원칙

5. **<span style = "color:violet">D</span>IP(Dependency Inversion Principle)** : 의존 역전 원칙

<br><br>

## SOLID 원칙의 중요성과 적용 효과
---

**좋은 소프트웨어**란 변화에 잘 대응하는 것을 말한다. 변화에 효과적으로 대응하기 위해서는 소프트웨어 설계의 근본적인 품질이 중요하다.<br>
**좋은 설계**는 시스템이 새로운 요구사항, 변경사항이 발생했을 때 영향을 받는 범위를 최소화 하는 구조이다.<br> 시스템이 예상치 못한 변경사항에 직면하더라도 유연하게 대응할 수 있고, 확장 가능한 구조를 갖추는 것이 핵심이다.
<br>
이러한 요구를 충족시키기 위해 SOLID 원칙이 중요하다. 다음은 SOLID 원칙을 적용했을 때 얻을 수 있는 효과이다.

1. **유연한 변경 대응** : 각 원칙은 소프트웨어의 구조를 정리하고, 변경 사항이 최소한의 영향을 미치도록 설계한다.
2. **효율적인 확장과 유지보수** : 기존 코드를 수정하지 않고도 새로운 기능을 추가할 수 있도록 하여, 시스템의 유연성을 증가시킨다.
3. **불필요한 복잡성 제거** : 리팩토링에 소요되는 시간을 단축시켜, 개발 생산성을 높이고, 유지보수 비용을 절감한다.

<br><br>

# **<span style = "color : purple"> S.O.L.I.D</span>**
 
### 단일 책임 원칙 - SRP(Single Responsibility Principle)
---
- [x] 클래스(객체)는 단 하나의 **책임**만 가져야 한다.
    > 여기서, '책임'의 의미는 '기능 담당'이다.

    <br>

- [x] **하나의 클래스는 하나의 기능을 담당하여 하나의 책임을 수행**하는데 집중되도록 클래스를 따로따로 여러개 설계하라는 원칙이다.
  <br>

- [x] 만일 하나의 클래스에 기능이 여러개 있다면 기능 변경이 일어났을 때 수정해야할 코드가 많아지는데, SRP원칙을 따름으로써 **한 책임의 변경으로부터 다른 책임의 변경으로의 연쇄작용을 극복**할 수 있다.
<br>

- [x] 단일 책임 원칙의 목적은 **프로그램 유지보수성을 높이기 위함**에 있다.

<br>

- [x] 한 클래스는 한 가지의 책임에 관한 변경사항이 생겼을 때만 코드를 수정하게 되는 구조가 좋은 구조이다.

<br>

- [x] 클래스를 세세하게 나눔으로써 전체 코드 길이가 길어졌다 하더라도, 하나의 클래스를 사용하는 것보다 여러 개의 클래스를 사용하는 것이 더 효율적이다

<br>

- [x] SRP 원칙은 **코드의 가독성을 향상** 시켜주고, **유지보수를 용이**하게 해주며, **다른 설계 원리들을 적용하는 기초**가 되는 원칙이다.

<br><br>


### 개방 폐쇄 원칙 - OCP(Open Closed Principle)
---
- [x] **'클래스는 확장에는 열려있어야 하며, 수정에는 닫혀있어야 한다.'**
    > [확장에 열려있다] : 새로운 변경 사항이 발생했을 때 유연하게 코드를 추가함으로써 큰 힘을 들이지 않고 애플리케이션의 기능을 확장할 수 있음
    > [수정에 닫혀있다] : 새로운 변경 사항이 발생했을 때 객체를 직접적으로 수정을 제한함
    > 확장 : 새로운 기능이 추가됨

    <br>

- [x] 기능 추가 요청이 오면 **클래스를 확장을 통해 손쉽게 구현**하면서, **확장에 따른 클래스 수정은 최소화** 하도록 프로그램을 작성해야 하는 설계 기법이다.
> 기존의 코드를 변경하지 않으면서, 기능을 추가할 수 있도록 설계되어야 함

<br>

- [x] 한마디로, **OCP 원칙은 추상화 사용을 통한 관계 구축 권장**을 의미하는 것이다.
<br>

- [x] **다형성과 확장**을 가능케 하는 객체지향의 장점을 극대화하는 기본적인 설계 원칙
<br>

    >💡
    자바 프로그래밍을 배우면서 사용한 추상화 클래스와 상속을 통한 클래스 관계 구축을 말하는 것

<br><br>

### 리스코프 치환 원칙 - LSP(Liskov Substitution Principle)
---
- [x] **서브 타입은 언제나 기반(부모) 타입으로 교체**할 수 있어야 한다.
**다형성 원리를 이용하기 위한 원칙!**

<br>

- [x] **다형성의 특징을 이용**하기 위해, 상위 클래스 타입으로 객체를 선언하여 하위 클래스의 인스턴스를 받으면, **업캐스팅된 상태에서 부모의 메서드를 사용해도 동작이 의도대로** 흘러가야 하는 것을 의미 함
> 업캐스팅 : 자식 클래스에 있는 객체가 부모 클래스 타입으로 형변환 되는 것을 말한다.

<br>

- [x] LSP 원칙은 부모 메서드의 오버라이딩을 조심스럽게 따져가며 해야한다.
부모 클래스와 동일한 수준의 선행 조건을 기대하고 사용하는 프로그램 코드에서 예상치 못한 문제를 일으킬 수 있기 때문이다.

<br>

- [x] 모든 코드에서 LSP를 지키기는 **어렵다**.

<br>


>💡
ex. Collection Interface
>> Collection 타입의 객체에서 자료형을 LinkedList에서 전혀 다른 자료형 HeadSet으로 바꿔도 add() 메서드를 실행하는데 있어 원래 의도대로 작동되기 때문이다.

<br>

``` java
public void myData() {
	// Collection 인터페이스 타입으로 변수 선언
    Collection data = new LinkedList();
    data = new HashSet(); // 중간에 전혀 다른 자료형 클래스를 할당해도 호환됨
    
    modify(data); // 메소드 실행
}

public void modify(Collection data){
    list.add(1); // 인터페이스 구현 구조가 잘 잡혀있기 때문에 add 메소드 동작이 각기 자료형에 맞게 보장됨
    // ...
}
```
<br><br>


### 인터페이스 분리 원칙 - ISP(Interface Segregation Principle)
---

> 인터페이스 : 일종의 추상 클래스로, 추상 메서드를 갖지만 추상화 정도가 높아 일반 메서드 또는 멤버 변수를 구성원으로 가질 수 없음


- [x] **인터페이스를 각각 사용에 맞게 끔 잘게 분리**해야한다.

<br>

- [x] SRP 원칙이 **클래스의 단일 책임**을 강조한다면, ISP는 **인터페이스의 단일 책임**을 강조하는 것으로 보면 된다.
SRP 원칙의 목표는 클래스 분리를 통하여 이루어 진다면, ISP 원칙은 인터페이스 분리를 통해 설계하는 원칙이다.

<br>

- [x] ISP 원칙의 목표는 인터페이스를 사용하는 클라이언트를 기준으로 분리함으로써, **클라이언트의 목적과 용도에 적합한 인터페이스 만을 제공**하는 것이다.

<br>

- [x] 주의해야 할점은 **한번 인터페이스를 분리하여 구성해놓고 나중에 무언가 수정사항이 생겨서 다시 인터페이스들을 분리하는 행위**를 가하지 말아야 한다.
(인터페이스는 한번 구성하였으면 웬만해선 변하면 안되는 정책 개념이다.)

<br>

>💡
인터페이스는 제약 없이 자유롭게 다중 상속(구현)이 가능하기 때문에, 분리할 수 있으면 분리하여 각 클래스 용도에 맞게 implements 하라는 설계 원칙이다.
>> implements(interface 구현):
부모 객체는 선언만 하며 정의(내용)은 자식에서 오버라이딩(재정의)해서 사용해야 함


<br><br>

### 의존 역전 원칙 - DIP(Dependency Inversion Priciple)
---

- [x] 어떤 Class를 참조하여 사용해야하는 상황이 생긴다면, 그 Class를 직접 참조하는 것이 아니라, 그 **대상의 상위 요소(추상 클래스 or 인터페이스)로 참조**하는 것이다.
> 구현 클래스에 의존 X, **인터페이스에 의존**!

<br>

- [x] 객체들이 서로 정보를 주고 받을 때는 의존 관계가 형성된다. 이 때 객체들은 **나름대로의 원칙**을 갖고 정보를 주고 받아야 하는 약속이 있다. 여기서 나름대로의 원칙이란 **추상성이 높은 클래스와 통신**을 한다는 것을 의미한다.

<br>

- [x] 의존 관계를 맺을 때 변화하기 쉬운 것 또는 자주 변화하는 것보다는, <span style = "color : #9999FF">변화하기 어려운 것 & 거의 변화가 없는 것</span>에 의존하라는 것이다.

<br>

- [x] 직접 인스턴스를 가져다 쓰게 되면, 하위 모듈의 구체적인 내용에 클라이언트가 의존하게 되어 하위 모듈에 변화가 있을 때마다 **클라이언트나 상위 모듈의 코드를 자주 수정**해야 되기 때문이다.

<br>

>💡
의존 역전 원칙의 지향점은 각 클래스간의 결합도를 낮추는 것이다.

<br>

## Impl 파일

service 패키지를 구성할 때 Interface와 Impl 구현 클래스로 구분하여 작성함

**확장성 보장**
Interface-Impl 구조를 가져가게 되면 인터페이스를 정해두고 해당 구현을 여러 모듈로 할 수 있음

하나의 인터페이스에 대하여 독립된 구현체를 여러 개 사용할 수 있게 되어 개발 환경에서의 모듈과 실제 배포 단계에서의 모듈 로직을 다르게 구성하면서도, 이를 사용하는 레벨에서는 같은 결과를 보장할 수 있음

구현체와 인터페이스를 구분함으로써 유연성을 확보한다고 이해할 수 있음

**협업 원활**


<br><br><br>

---
>출처
[객체 지향 설계의 5가지 원칙 - S.O.L.I.D](https://inpa.tistory.com/entry/OOP-%F0%9F%92%A0-%EA%B0%9D%EC%B2%B4-%EC%A7%80%ED%96%A5-%EC%84%A4%EA%B3%84%EC%9D%98-5%EA%B0%80%EC%A7%80-%EC%9B%90%EC%B9%99-SOLID)
[완벽하게 이해하는 SRP (단일 책임 원칙)](https://inpa.tistory.com/entry/OOP-%F0%9F%92%A0-%EC%95%84%EC%A3%BC-%EC%89%BD%EA%B2%8C-%EC%9D%B4%ED%95%B4%ED%95%98%EB%8A%94-SRP-%EB%8B%A8%EC%9D%BC-%EC%B1%85%EC%9E%84-%EC%9B%90%EC%B9%99)
[완벽하게 이해하는 OCP (개방 폐쇄 원칙)](https://inpa.tistory.com/entry/OOP-%F0%9F%92%A0-%EC%95%84%EC%A3%BC-%EC%89%BD%EA%B2%8C-%EC%9D%B4%ED%95%B4%ED%95%98%EB%8A%94-OCP-%EA%B0%9C%EB%B0%A9-%ED%8F%90%EC%87%84-%EC%9B%90%EC%B9%99)
[완벽하게 이해하는 LSP (리스코프 치환 원칙)](https://inpa.tistory.com/entry/OOP-%F0%9F%92%A0-%EC%95%84%EC%A3%BC-%EC%89%BD%EA%B2%8C-%EC%9D%B4%ED%95%B4%ED%95%98%EB%8A%94-LSP-%EB%A6%AC%EC%8A%A4%EC%BD%94%ED%94%84-%EC%B9%98%ED%99%98-%EC%9B%90%EC%B9%99)
[완벽하게 이해하는 ISP (인터페이스 분리 원칙)](https://inpa.tistory.com/entry/OOP-%F0%9F%92%A0-%EC%95%84%EC%A3%BC-%EC%89%BD%EA%B2%8C-%EC%9D%B4%ED%95%B4%ED%95%98%EB%8A%94-ISP-%EC%9D%B8%ED%84%B0%ED%8E%98%EC%9D%B4%EC%8A%A4-%EB%B6%84%EB%A6%AC-%EC%9B%90%EC%B9%99)
[완벽하게 이해하는 DIP (의존 역전 원칙)](https://inpa.tistory.com/entry/OOP-%F0%9F%92%A0-%EC%95%84%EC%A3%BC-%EC%89%BD%EA%B2%8C-%EC%9D%B4%ED%95%B4%ED%95%98%EB%8A%94-DIP-%EC%9D%98%EC%A1%B4-%EC%97%AD%EC%A0%84-%EC%9B%90%EC%B9%99)