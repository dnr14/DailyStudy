# 스프링 부트로 배우는 자바 웹 개발

## 2.1 서블릿 시작하기 && 2.2.1 서블릿 생면 주기<br>

서블릿이란?<br>

<Strong>클라이언트</Strong>의 요청을 처리하고 그 결과를 다시 클라이언트에게 전송하는 Servlet클래스의 구현 규칙을 지킨 자바 프로그래밍 기술
이다<br>

JSP와 Servlet의 차이를 물어보는 분이 종종 있었다. 자세히 들어가면 복잡하지만 간단히 차이만 말하면 Servlet은 Java언어 안에 html를 넣은 구조(?)
JSP는 html안에 Java코드를 넣어놓은 방식이다.< 


### 서블릿 생명 주기<br>

Servlet은 생명주기를 가지고 있다. WAS에서 Context가 초기화되면서 생명주기가 시작된다.<br>
생명주기는 3단계로 <Strong>Initialize, Service, Destory</Strong>로 구성이된다.

#1. init
```java
@WebServlet(
	name="initServlet", 
	urlPatterns={"/init"}, 
	initParams = {@WebInitParam(name = "siteName", value = "jpub")}
	)
public class InitServlet extends HttpServlet{

    @Override
    public void init(ServletConfig servletConfig) throws ServletException{
        System.out.println("init call");
     
    }
}
```

기본적으로 HttpServlet클래스를 상속을 받아서 init메소드를 오버라이드 해준다.
서블릿 3.0부터는 어노테이션으로 매핑을 해줄수 있게 되었다. 
아래 버전은 밑에 web.xml 파일에 초기화 변수를 설정할 수있다.

```xml
	<servlet>
		<servlet-name>initServlet</servlet-name>
		<servlet-class>info.thecodinglive.basic</servlet-class>
		<init-param>
			<param-name>siteName</param-name>
			<param-value>jpub</param-value>
		</init-param>
	</servlet>
	<servlet-mapping>
		<servlet-name>initServlet</servlet-name>
		<url-pattern>/init</url-pattern>
	</servlet-mapping>
```
