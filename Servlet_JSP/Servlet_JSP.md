JSP(Java Server Pages)란
Java 언어를 기반으로 하는 Server Side 스크립트 언어

HTML 코드에 Java 코드를 넣어 동적인 웹 페이지를 생성하는 웹 어플리케이션 도구
JSP를 통해 정적인 HTML과 동적으로 생성된 contents(HTTP 요청 파라미터)를 혼합하여 사용할 수 있다.
즉, 사용자가 입력한 contents에 맞게 동적인 웹 페이지를 생성한다.

Servlet 기술의 확장
Servlet를 보완한 스크립트 방식 표준
Servlet의 모든 기능 + 추가적인 기능

JSP의 내부적인 동작 과정
JSP 문서는 백그라운드에서 Servlet으로 자동으로 변환된다.

JSP가 실행되면 WAS는 내부적으로 JSP 파일을 Java Servlet(.java)으로 변환한다.
WAS는 이 변환한 Servlet을 동작하여 필요한 기능을 수행한다.
Servlet의 동작 (Servlet 이란 참고)
1) WAS는 사용자 요청에 맞는 적절한 Servlet 파일을 컴파일(.class 파일 생성)한다.
2) .class 파일을 메모리에 올려 Servlet 객체를 만든다.
3) 메모리에 로드될 때 Servlet 객체를 초기화하는 init() 메서드가 실행된다.
4) WAS는 Request가 올 때마다 thread를 생성하여 처리한다.
5) 각 thread는 Servlet의 단일 객체에 대한 service() 메서드를 실행한다.
6) service() 메서드는 요청에 맞는 적절한 메서드(doGet, doPost 등)를 호출한다.
수행 완료 후 생성된 데이터를 웹 페이지와 함께 클라이언트로 응답한다.
JSP의 특징
스크립트 언어이기 때문에 자바 기능을 그대로 사용할 수 있다.
Tomcat(WAS)이 이미 만들어놓은 객체(predefined values)를 사용한다.
Ex. request, response, session 등
아래 참고1
사용자 정의 태그(custom tags)를 사용하여, 보다 효율적으로 웹 사이트를 구성할 수 있다.
JSTL(JSP Standard Tag Library, JSP 표준 태그 라이브러리)사용
아래 참고2
HTML 코드 안에 Java 코드가 있기 때문에 HTML 코드를 작성하기 쉽다.
Servlet과 다르게 JSP는 수정된 경우 재배포할 필요 없이 Tomcat(WAS)이 알아서 처리해준다.
참고1 Predefined Values(또는 Implicit Object)

미리 정의된 객체로, WAS가 제공하는 객체를 의미한다.
request: the HttpServletRequest Object
response: the HttpServletResponse Object
session: the HttpSession Object
out: the PrintWriter Object
application: the ServletContext Object
구체적인 내용은 www.javatpoint.com 참고
JSP 문법
1. JSP Expression
<%= expression %>

JSP Expression element는 String으로 변환되어 Servlet의 출력에 삽입된다.
동적인 페이지를 생성한다.
끝에 세미콜론(;)을 붙이지 않는다.

2. JSP Scriptlet
<% code fragment %>

간단한 값이 아닌 조금 더 복잡한 것을 수행하고자 할 때 JSP Scriptlet을 사용한다.
임의의 Java 코드를 삽입할 수 있다.
JSP Scriptlet Tag는 메서드가 아닌 변수만 선언할 수 있다.

3. JSP Declaration
<%! declaration %>

JSP Declaration을 사용하면 Servlet 클래스에 삽입되는 메서드나 필드를 정의할 수 있다.
JSP Scriptlet Tag와 달리 JSP Declaration Tag는 메서드와 변수 모두 선언할 수 있다.

4. JSP Comment
<%-- comment --%>

주석의 개념
5. JSP Directive
<%@ directive %>

JSP 페이지의 전체적인 구조에 영향을 미친다.
전체 구조에 대해 WAS에 지시를 내린다.
지시어에 들어가는 것: page, include, taglib

page
<%@ page attribute = "value" %>
page 지시어는 Container에 명령을 제공하는데 사용된다.
include
<%@ include file = "relative_url" %>
include 지시어는 변환 단계에서 다른 외부 파일의 내용을 현재 JSP에 병합하도록 Container에 지시한다.
웹 페이지에서 header와 footer의 구성은 거의 동일하기 때문에 외부에서 형식을 만든 후 include 지시어를 이용하여 main.jsp에 병합한다.
taglib
<%@ taglib uri = "uri" prefix = "prefixOfTag" %>
JSP API를 사용하면 HTML 또는 XML 태그처럼 보이는 사용자 정의 태그(custom tags)를 정의할 수 있다.
JSTL(JSP Standard Tag Library, JSP 표준 태그 라이브러리)사용
아래 참고2
tag library는 사용자가 정의한 동작을 구현한 사용자 정의(user-defined) 태그 집합입니다.
6. JSP Action
JSP Action XML 구문 안의 구조들을 사용하여 WAS의 동작을 제어한다.
<jsp:forward> action
다른 리소스(JSP, html 또는 Servlet과 같은 정적 페이지)로 요청을 전달하는데 사용한다.
<jsp:include> action
현재 JSP 페이지에 다른 리소스를 포함시키는데 사용한다.
<jsp:useBean> action
해당하는 Bean(자바 객체)이 이미 존재하는지 확인한다.
객체가 없으면 지정된 객체를 생성한다.
<jsp:setProperty> action
Bean(자바 객체)의 속성을 설정한다.
<jsp:getProperty> action
주어진 속성값을 가져오는데 사용되며 이를 문자열로 변환하고 동적인 웹 페이지를 생성하는데 해당 내용을 사용할 수 있다.
용도
1) 동적으로 파일을 삽입하고
2) JavaBeans 구성 요소를 재사용하고
3) 사용자를 다른 페이지로 전달(forward)할 수 있다.
예시

구체적인 예시는 www.javatpoint.com 참고
JSP에서 동적인 코드를 호출하는 6가지 전략
1번 -> 6번으로 갈수록
간단한 app 또는 작은 규모의 개발팀 -> 복잡한 app 또는 큰 규모의 개발팀(Enterprise)

Call Java code directly
Java 코드를 직접 호출
모든 Java 코드를 JSP 페이지에 넣는다.
아주 적은 양의 코드에만 적합한 전략
Call Java code indirectly
Java 코드를 간접적으로 호출
별도의 utility class(Java Class)를 작성한다.
utility class를 호출하는 데 필요한 Java 코드만 JSP 페이지에 넣는다.
Use beans
beans로 구조화된 별도의 utility class(Java Class)를 작성한다.
jsp:useBean, jsp:getProperty, jsp:setProperty를 사용하여 utility class를 호출한다.
Use the MVC architecture
MVC 아키텍처를 사용
Servlet(Controller)이 요청에 응답하고 적절한 데이터를 검색하여 결과를 beans(Model)에 저장한다.
이 결과를 JSP 페이지(View)로 전달하여 결과를 표시한다.
즉, JSP 페이지는 bean을 사용한다.

구체적인 MVC 패턴은 MVC-Architecture 참고
Use the JSP expression language
shorthand syntax를 이용하여 간단하게 객체 속성(property)에 접근하고 출력한다.
즉, jsp:useBean, jsp:getProperty, jsp:setProperty를 expression language으로 간단하게 표현할 수 있다.
일반적으로 beans, MVC 패턴을 함께 사용한다.
Use custom tags
tag handler class를 만든다.
XML과 같은 사용자 정의 태그(custom tags)를 사용하여 태그 핸들러를 호출한다.
JSP Action 태그와 JSP EL(Expression Language)
객체 Bean에 접근하는 방법

1. JSP Action 태그
위의 JSP 문법 참고
2. JSP EL(Expression Language)
JSP 2.0의 주요 구성 요소 중 하나
EL을 사용하면 Java Beans 구성 요소에 저장된 응용 프로그램 데이터에 쉽게 접근할 수 있다.
객체 접근: ${ObjectName}
property에 접근: ${ObjectName.property}
예시
JSP Action 태그 이용
<%-- JSP 1.2(old) --%>
<jsp:useBean id="customer" type="beans.Customer" scope="request"> 
</jsp:useBean>

<ul>
  <li>Name: <jsp:getProperty name="customer" property="name" /></li>
  <li>Email: <jsp:getProperty name="customer" property="email" /></li>  
  <li>ID: <jsp:getProperty name="customer" property="id" /></li>
</ul>  
JSP EL(Expression Language) 이용
<%-- JSP 2.0(Preferred)  --%>
<ul>
  <li>Name: ${customer.name}</li>
  <li>Email: ${customer.email}</li>  
  <li>ID: ${customer.id}</li>
</ul> 
JSP Scriptlet 태그와 JSTL(JSP Standard Tag Library)
복잡한 것을 수행하는 임의의 Java Code를 삽입하는 방법

1. JSP Scriptlet 태그
위의 JSP 문법 참고
2. JSTL(JSP Standard Tag Library) 참고2
많은 JSP 애플리케이션의 공통적인 핵심 기능을 캡슐화하는 유용한 JSP 태그 모음(JSP 표준 태그 라이브러리)
즉, JSP 페이지를 작성할 때 유용하게 사용할 수 있는 여러 가지 action과 함수가 포함된 라이브러리
가장 많이 사용하는 태그 확장 라이브러리
자신만의 Custom Tag를 추가할 수 있는 기능을 제공한다.
사용하는 이유?
JSP에 Java Code가 들어가는 것을 막기 위해서 사용한다.
즉, Java Code(JSP Scriptlet)대신 Tag를 사용하여 프로그래밍할 수 있도록 하기 위해 도입되었다.
JSTL 태그의 분류
Core
Formatting tags
SQL tags
XML tags
JSTL Functions
구체적인 내용은 www.tutorialspoint 참고
taglib 지시어를 사용하여 JSP 페이지가 Custom 태그 집합을 사용한다고 선언한다.
Java Code 대신 Custom Tag를 사용한다.
prefix를 설정하여 여러 개의 tag library를 식별한다.
즉, 어떤 라이브러리를 사용하는지 알 수 있다.
<%@ taglib uri=http://java.sun.com/jsp/jstl/core prefix="c" %> 

<c:out value="Hello World"> </c:out>
<!-- Similar to the way <%= "Hello World" %> works -->
예시
JSP Scriptlet 태그 이용
<html>
<head>
<title>Count to 10 in JSP scriptlet</title>
</head>
<body>
   <%
      for(int i=1;i<=10;i++){
   %>
   <%=i%><br/>
   <%
      }
   %>
</body>
</html>
JSTL(JSP Standard Tag Library) 이용
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c"%>
<html>
<head>
<title>Count to 10 Example (using JSTL)</title>
</head>
<body>
   <c:forEach var="i" begin="1" end="10" step="1">
      <c:out value="${i}"/>
      <br/>
   </c:forEach>
</body>
</html>
관련된 Post
https://gmlwjd9405.github.io/2018/11/03/jsp.html
