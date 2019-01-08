용어정리
===
### Dependency
  * Dependency(또는 의존성)는 코드에서 두 모둘간의 연결이라고 볼 수 있다. 객체 지향 언어에서는 두 클래스간의 관계라고도 말한다.
  * 일반적으로 둘 중 하나가 다른 하나를 어떤 용도를 위해 사용한다. 간단히 생성자 호출인 new 연산자가 될 수 있다.
  * 클래스 내에서 개발자가 객체를 직접 관리(생성 및 조작)할 경우, 의존성이 나타나게 된다.
  * A 클래스와 B 클래스와 C 클래스가 있다고 가정하면, A 클래스 내에서 B 객체와 C 객체를 생성할 경우, A 객체는 B 객체와 C 객체를 사용함과 동시에 의존한다 라는 의미를 가진다.

    ```java
    public class A {	
      public A() {
        B b = new B();
	    C c = new C();
      }
    }
    ```
  * 위와 같은 경우, A 객체는 객체 B와 C에 의존하게 되는 경우가 생깁니다. 이런 의존성이 위험한 이유는 다음과 같습니다.

#### Dependency가 위험한 이유

* 의존성이 강하면 강할수록, 상호적으로 결합이 생기고, 결합이 강해지면 클래스간의 관계가 복잡해지고 쉽사리 변경하기가 쉽지가 않다.
* 두 코드가 서로를 종속하고 있기 때문에 변경에 대한 작업이 어려워진다. 
* A 객체에서 다른 객체를 사용한다고 했을 때 테스트를 한다고 해보자, 테스트가 실패했을 때 현재 객체에서의 실패일까 의존하는 객체의 실패일까? 알 수 없다. 이게 클래스별로 상당한 양의 코드라면 이건 너무 심각한 문제가 된다.
* 하나의 모듈이 바뀌면 의존한 다른 모듈까지 변경이 이루어지기 때문이다.  
<br>

### DI(Dependency Injection)

* A 클래스가 B와 C 객체에 의존하고 있는 상황일 때, 직접 A 클래스 내에서 B객체와 C객체를 생성하는 것이 아니라, 외부에서 B 객체와 C 객체를 생성한 다음 A 클래스에 주입하는 방법이다.
* 의존 객체를 외부에서 직접 생성해서 주입하는 형태를 의존성 주입이라고 한다.
* 그렇게 할 경우, 외부(프레임워크)에 의해 의존 객체가 동적으로 주입되므로, 여러 객체간의 결합(의존도)이 줄어든다.
* 의존성 주입을 위해서는 객체를 생성하고 넘겨주는 외부의 무언가가 필요하게 되는데, 우리는 Spring Framework에서 이를 해결한다.
* 의존 객체를 생성하고 주입시켜 주는 곳이 Spring에서는 Bean container가 된다.

#### Dependency Injection의 장점

* 종속성(의존성)이 줄어든다
  * 종속성이 줄어드므로, 변경에 민감하지가 않다.

* 재사용성이 증가한다.
  * 다른 클래스에서도 이러한 의존 객체가 필요할 경우, Bean 컨테이너에서 의존 객체를 주입해줄 수 있다.

* 테스트 코드를 작성하는데에 대한 불편이 줄어든다.
* 코드의 가독성이 올라간다. 
<br>

### Build
  * 소스코드 파일을 컴퓨터에서 실행시킬 수 있도록 가공하는 것, 실행가능한 파일을 만드는 것.
<br>

### REST API
  * 웹 설계의 우수성을 제대로 사용하기 위한 Architecture
<br>

### JPA(Java Persistent API)
  * 어플리케이션과 JDBC 사이에서 동작하는 도구
  * 자바 플랫폼 SE와 자바 플랫폼 EE를 사용하는 응용프로그램에서 관계형 데이터베이스의 관리를 표현하는 자바 API이다. 
  * 기존에 EJB에서 제공되던 엔터티 빈을 대체하는 기술이다.
  * ORM 표준 기술로 Hibernate, OpenJPA, EclipseLink, TopLink Essentials과 같은 구현체가 있고 이에 표준 인터페이스가 바로 JPA이다.
  * ORM(Object Relational Mapping)이란 RDB 테이블을 객체지향적으로 사용하기 위한 기술이다. 
  * RDB 테이블은 객체지향적 특징(상속, 다형성, 레퍼런스, 오브젝트 등)이 없고 자바와 같은 언어로 접근하기 쉽지 않다.
  * 때문에 ORM을 사용해 오브젝트와 RDB 사이에 존재하는 개념과 접근을 객체지향적으로 다루기 위한 기술이다.
<br>

### Gradle
  * 소스 코드로 부터 배포 가능한 산출물을 빌드하는 '빌드툴' 또는 '프로젝트 관리 도구'
  * Gradle = Ant의 유연성 + Maven의 편리성을 조합해서 만든 빌드 시스템
  * API 제공 및 확장성이 좋다.
  * 빌드의 구조화를 제공하고, Mulit-Project 빌드를 쉽게할 수 있도록 제공
  * Groovy DSL(Domain Specific Language) 기반
  * 빌드 스크립트는 기존 XML이 아닌 Grooovy 방식으로 작성
<br>

### Rest Controller
  * REST(Representational State Transfer)는 하나의 URI는 하나의 고유한 리소스를 대표하도록 설계된다는 개념이다.
  * REST 방식은 특정한 URI는 반드시 그에 상응하는 데이터 자체라는 것을 의미하는 방식이다.
    * /wedul/123은 해당 페이지의 번호의 123번이라는 고유한 의미를 가지고 설계하고, 이에 대한 처리는 GET, POST 방식과 같이 추가적인 정보를 통해서 결정한다.

  * Rest API는 외부에서 위와 같은 방식으로 특정 URI를 통해서 사용자가 원하는 정보를 제공하는 방식이다.
    * Rest 방식의 서비스 제공이 가능한 것을 RestFul 하다고 표현한다.

  * 스프링 3부터 @Repository 어노테이션을 지원하면서 REST 방식의 처리를 지원하고 있었으며 스프링 4에 들어와서 @RestController가 본격적으로 소개되었다.
  * @RestController
    * 특정한 JSP와 같은 뷰를 만들어 내는 것이 아닌 REST 방식의 데이터 자체를 서비스하는 것을 말한다.
    * @Controller + @ResponseBody 의 축약형으로써, 리턴값을 view resolver로 매핑하지 않고 그대로 출력해준다.
    * @RestController라는 어노테이션을 컨트롤러에 지정하면, 해당 컨트롤러의 모든 메소드는 자동적으로 @RseponseBody 어노테이션이 적용된 것처럼 동작한다.
    * @RestController가 적용된 컨트롤러의 모든 메소드는 jsp등의 뷰를 생성하지 않고 데이터만 반환하게 된다.
    * 이 데이터는 크게 단순문자열, JSON, XML 등으로 나누어진다.
    * @Controller와 RESTful 컨트롤러인 @RestController의 차이점은 HTTP Response Body가 생성되는 방식이다.
    * @Controller 는 View Page를 반환하지만, @RestController는 객체(VO,DTO)를 반환하기만 하면, 객체데이터는 application/json 형식의 HTTP ResponseBody에 직접 작성되게 된다.
<br>

### GetMapping
  * @RequestMapping(method = RequestMethod.GET) 의 축약형으로써, 애너테이션만 보고 무슨 메소드 요청인지 바로 알아볼 수 있다.
