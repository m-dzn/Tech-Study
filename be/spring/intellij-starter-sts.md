# IntelliJ Starter (STS)

## IntelliJ Starter (STS)

### 프로젝트 생성

![메뉴 → File → New Project → Maven 프로젝트 & java 1.8 버전 선택](https://files.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-MXegyfBR1nI\_53AOjXG%2F-MXetwhXV3EJGKlu27U3%2F-MXgbd30tMtVnBZBQjIn%2Fimage.png?alt=media\&token=12b14775-30ba-4d06-9f9b-a2a6d5b5e469)

![프로젝트 저장 경로 및 Artifact 정보 설정 → Finish로 프로젝트 생성](https://files.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-MXegyfBR1nI\_53AOjXG%2F-MXetwhXV3EJGKlu27U3%2F-MXgc4RK-K58QdiKtz-B%2Fimage.png?alt=media\&token=03de7f6d-feb0-488f-b537-f47a051fcd4d)

### IntelliJ 설정 변경

#### 디렉토리 구조 변경

1. root에 위치한 web 디렉토리를 → src\main으로 이동시킵니다.
2. web → webapp으로 디렉토리명을 변경합니다.
3. webapp 하위 디렉토리 구조를 정리합니다.
   * WEB-INF\spring-config 디렉토리로 applicationContext.xml 이동
   * WEB-INF\spring-config\appServlet 디렉토리로 dispatcher-servlet.xml 이동

![디렉토리 구조 변경 (IntelliJ → STS Spring MVC)](https://files.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-MXegyfBR1nI\_53AOjXG%2F-MXge0vCdVdHzH6r0BYy%2F-MXgfC7qHNzsRsRHQxBi%2Fimage.png?alt=media\&token=45aefcd2-058e-4807-a903-2f86a5cbe6e6)

#### web.xml 설정 변경

* applicationContext.xml의 경로를 재설정합니다.
  * /WEB-INF/spring-config/applicationContext.xml
* dispatcher-servlet.xml의 경로를 재설정합니다.
  * /WEB-INF/spring-config/appServlet/dispatcher-servlet.xml

```markup
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee http://xmlns.jcp.org/xml/ns/javaee/web-app_4_0.xsd"
         version="4.0">

    <!-- MVC root 설정 파일 경로 변경 -->
    <context-param>
        <param-name>contextConfigLocation</param-name>
        <param-value>/WEB-INF/spring-config/applicationContext.xml</param-value>
    </context-param>
    <listener>
        <listener-class>org.springframework.web.context.ContextLoaderListener</listener-class>
    </listener>

    <!-- DispatcherServlet 설정 파일 경로 변경 -->
    <servlet>
        <servlet-name>dispatcher</servlet-name>
        <servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
        <init-param>
            <param-name>contextConfigLocation</param-name>
            <param-value>/WEB-INF/spring-config/appServlet/dispatcher-servlet.xml</param-value>
        </init-param>
        <load-on-startup>1</load-on-startup>
    </servlet>

    <!-- DispatcherServlet 기본 url 패턴 변경 -->
    <servlet-mapping>
        <servlet-name>dispatcher</servlet-name>
        <url-pattern>/</url-pattern>
    </servlet-mapping>

    <!-- encoding filter -->
    <filter>
        <filter-name>encodingFilter</filter-name>
        <filter-class>
            org.springframework.web.filter.CharacterEncodingFilter
        </filter-class>
        <init-param>
            <param-name>encoding</param-name>
            <param-value>UTF-8</param-value>
        </init-param>
    </filter>
    <filter-mapping>
        <filter-name>encodingFilter</filter-name>
        <url-pattern>/*</url-pattern>
    </filter-mapping>

</web-app>
```

#### 웹 리소스 경로 설정 변경

![Project Structure(Ctrl + Alt + Shift + s) → Modules](https://files.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-MXegyfBR1nI\_53AOjXG%2F-MXghX7mPaea6ME24Q5d%2F-MXghjbSzb8Y-w-k6\_I-%2Fimage.png?alt=media\&token=611c284f-918d-4c67-b22a-33763e449b70)

Web Resource Directory의 붉은색 글씨를 더블 클릭하면 아래의 창이 나타납니다.

![리소스 디렉토리 경로 변경 : root 디렉토리￦src￦main￦webapp](https://files.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-MXegyfBR1nI\_53AOjXG%2F-MXghX7mPaea6ME24Q5d%2F-MXgjV5J1oHll4tF9-UQ%2Fimage.png?alt=media\&token=f87be809-4ae4-4abe-89e6-d68a83cf5dec)

web 폴더의 경로를 옮기고

폴더 이름을 webapp으로 바꿨으므로

directory path를 알맞게 수정해준 후 OK를 눌러빠져나옵니다.

#### Tomcat 서버 추가

![빨갛게 표시된 Run/Debug Configurations 클릭](https://files.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-MXegyfBR1nI\_53AOjXG%2F-MXgli915AZyOjgZHaZ3%2F-MXgmG5SRYCM47E7iU3Z%2Fimage.png?alt=media\&token=cbdbdb03-c154-4486-baa6-003b17492b4f)

![+ 버튼 클릭 → Add New Configuration → Tomcat Local Server 생성](https://files.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-MXegyfBR1nI\_53AOjXG%2F-MXgli915AZyOjgZHaZ3%2F-MXgnqaVw9dZNoHdXY2I%2Fimage.png?alt=media\&token=80ed7b8d-2377-4176-a058-47ebb74860ae)

![](https://files.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-MXegyfBR1nI\_53AOjXG%2Fsync%2Fe63591477f751b5a076e0b09fe3460ffce4e1a2e.png?generation=1617809017415090\&alt=media)

**Warning: No artifacts marked for deployment 해결법**

FIX 버튼 클릭 → Deployment 탭 → Application context 수정 (baseUrl; 여기서는 " / ")

![](https://files.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-MXegyfBR1nI\_53AOjXG%2F-MXgoZZYtRmeFOAOYRH0%2F-MXgopZ1azxBTJvVPAzV%2Fimage.png?alt=media\&token=4864b4bf-0d9e-4f51-bbcd-c23ab872f623)

#### dispatcher-servlet.xml 설정

```markup
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:context="http://www.springframework.org/schema/context"
       xmlns:mvc="http://www.springframework.org/schema/mvc"
       xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd http://www.springframework.org/schema/context https://www.springframework.org/schema/context/spring-context.xsd http://www.springframework.org/schema/mvc https://www.springframework.org/schema/mvc/spring-mvc.xsd">

    <!-- 어노테이션 활성화 -->
    <mvc:annotation-driven />

    <!-- 컴포넌트를 스캔할 패키지 지정 -->
    <context:component-scan base-package="org.example.sts.controller" />

    <!-- 컨트롤러 prefix/suffix 지정 -->
    <bean class="org.springframework.web.servlet.view.InternalResourceViewResolver">
        <property name="prefix" value="/WEB-INF/views/"/>
        <property name="suffix" value=".jsp"/>
    </bean>

</beans>
```

#### pom.xml

Spring Framework 라이브러리를 추가합니다.

```markup
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.appleisle</groupId>
    <artifactId>basic-mall</artifactId>
    <version>1.0-SNAPSHOT</version>
    <name>Basic Mall</name>
    <url>http://maven.apache.org</url>

    <properties>
        <spring.version>5.2.3.RELEASE</spring.version>
    </properties>

    <dependencies>
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-web</artifactId>
            <version>${spring.version}</version>
        </dependency>
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-webmvc</artifactId>
            <version>${spring.version}</version>
        </dependency>

        <dependency>
            <groupId>junit</groupId>
            <artifactId>junit</artifactId>
            <version>4.11</version>
            <scope>test</scope>
        </dependency>
    </dependencies>

</project>
```

### 컨트롤러 & 뷰 파일 작성

#### Controller 파일 생성

경로 : org.example.sts.controller 패키

```java
package org.example.sts.controller;

import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.GetMapping;

@Controller
public class HomeController {

    @GetMapping("/home")
    public String home() {
        return "home";
    }

}
```

#### jsp 파일 생성

경로 : webapp/WEB-INF/views 폴더

```markup
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<head>
    <title>Home</title>
</head>
<body>
    <h1>Home.jsp 로드</h1>
</body>
</html>
```

![](https://files.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-MXegyfBR1nI\_53AOjXG%2Fsync%2F518d8e5d22b3c9dfec96ee37bb0db12c2f7d9d52.png?generation=1617809016859612\&alt=media)
