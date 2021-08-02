---
date: 2021-08-02

title: "Web Server vs Application Server"
excerpt: "about Web Server, Application and Web Service Architecture "

categories: WebServer
tags: web server, application server

toc: true  
toc_sticky: true
toc_label: "contents"
toc_icon : 

last_modified_at : 2021-08-02
---


## static page 와 dynamic page

![https://camo.githubusercontent.com/dac3eae0d749b45864d492ab82d046fbbfdf86891dc69dda6aaffdfabe9b5ea9/68747470733a2f2f676d6c776a64393430352e6769746875622e696f2f696d616765732f7765622f7374617469632d76732d64796e616d69632e706e67](https://camo.githubusercontent.com/dac3eae0d749b45864d492ab82d046fbbfdf86891dc69dda6aaffdfabe9b5ea9/68747470733a2f2f676d6c776a64393430352e6769746875622e696f2f696d616765732f7765622f7374617469632d76732d64796e616d69632e706e67)

**Static Pages**
- Web Server는 파일 경로를 받아, file contents를 반환
- 항상 동일한 페이지 반환(img, html, js.. 컴퓨터에 저장되어 있는 파일)

**Dynamic Pages**
- 인자에 맞는 동적인 contents를 반환
- 웹 서버에 의해 실행되는 프로그램을 통해 만들어진 결과물(컴퓨터에 저장되어 있는 파일x)
- Servlet: WAS 위에서 돌아가는 Java Program
- 개발자는 Servlet에 doGet()을 구현

## Web Server와 WAS
![https://gmlwjd9405.github.io/images/web/webserver-vs-was1.png](https://gmlwjd9405.github.io/images/web/webserver-vs-was1.png)

**Web Server의 개념**

- 하드웨어 : Web 서버가 설치되어 있는 컴퓨터
- 소프트웨어 : 웹 브라우저(클라이언트)로 부터 HTTP 요청을 받아 정적인 컨텐츠(html, js..)를 제공하는 컴퓨터 프로그램

**Web Server의 역할**

- HTTP 프로토콜을 기반하여 클라이언트의 요청(브라우저 or 크롤러)을 서비스 하는 기능을 담당
    1. 정적인 컨텐츠 제공(WAS를 거치지 않고, 자원 제공)
    2. 동적인 컨텐츠 제공을 위한 요청 전달, 클라이언트 요청(Request)를 WAS에 보내고, WAS가 처리한 결과를 클라이언트에게 전달(Response)한다.
- Web Server의 ex)Apache Server, Nginx, IIS

**WAS의 개념**

- DB 조회, 로직 처리를 요구하는 동적인 컨텐츠를 제공하기 위해 만들어진 Application Server
- HTTP를 통해 컴퓨터나 장치에 애플리케이션을 수행해주는 미들웨어(소프트웨어엔진)이다.
- "Web Container" or "Servlet Container"라고도 불린다.
    - Container란 JSP, Servlet을 실행시킬 수 있는 소프트웨어를 말한다.
    - 즉, WAS는 JSP, Servlet 구동 환경을 제공한다.

**WAS의 역할**

- WAS = Web Server + Web Container
- Web Server의 기능들을 구조적으로 분리하여 처리하는게 목적
    - 분산 트랜젝션, 보안, 메시징, 쓰레드 처리 등의 기능을 처리하는 분산 환경에서 사용된다.
    - 주로 DB서버와 같이 수행
    - 현재는 WAS가 가지고 있는 Web Server도 정적인 컨텐츠를 처리하는 데 있어서 성능상 큰 차이가 없다.

**WAS의 주요 기능**

- 프로그램 실행 환경, DB 접속 기능
- 여러 개의 트랜젝션 관리 기능

## Web Server와 WAS를 구분하는 이유  
  
**Web Server가 필요한 이유**

클라이언트에 이미지 파일을 보내는 과정

- 웹문서(HTML)이 클라이언트한테 보내질 때 정적인 파일들은 전송하지 않는다.
- 클라이언트는 HTML을 받고, 그에 맞게 필요한 것들을 서버에 요청 후  img 등 정적인 파일들을 받아온다.
- Web Server를 통해 img등 정적인 파일들을 Application Server까지 가지 않고 앞단에서 빠르게 받아온다.
- Web Server에서는 정적인 컨텐츠만 처리하도록 기능을 분산하여 서버에 부담을 줄인다.

**WAS가 필요한 이유**

- 웹 페이지에는 정적 컨텐츠와 동적 컨텐츠가 존재한다.

- Web Server만을 이용한다면, 사용자가 원하는 요청에 해당하는 모든 결과값을 미리 만들어놓고 서비스를 해야한다.

WAS를 통해 요청에 맞는 데이터를 DB에서 가져와서 비지니스 로직에 맞게 결과를 제공함으로서 자원의 효율적인 사용이 가능하다.

**Web Container와 Web Server의 동시 사용 이유**

1. 기능을 분리하여 서버 부하 방지
    - WAS는 DB조회, 로직 처리 등으로 바쁘기 때문에 Web Server을 이용하여 정적인 컨텐츠를 빠르게 제공하는것이 좋다
    - WAS는 기본적으로 동적인 컨텐츠를 처리하기 위해 존재한다.
    - 만약 WAS가 정적인 컨텐츠까지 처리한다면, 부하가 커져 동적인 컨텐츠의 처리 속도가 느려진다.
    - 이로 인해, 페이지 노출 시간이 늘어나게 된다.
2. 물리적으로 분리하여 보안 강화
    - SSL에 대한 암복호화 처리에 Web Server를 사용
3. 여러 대의 WAS를 연결 가능
    - Load Balancing을 위해서 Web Server를 사용
    - fail over, fail back 처리에 유리
    - 대용량 웹 어플리케이션(여러 개의 서버)의 경우 Web Server와 WAS를 분리 하여 무중단 운영을 위한 장애 극복에 쉽게 대응 ex) 앞 단의 Web Server에서 오류가 발생한 WAS를 이용하지 못하도록 한 후 WAS를 재시작함으로서 사용자는 오류를 느끼지 못하고 이용
4. 여러개의 웹 어플리케이션 서비스 가능
    - (하나의 서버에 PHP Application, Java Application 함께 사용)
5. 기타
    - 접근 허용 IP관리
    - 2대 이상의 서버에서의 세션 관리 등 Web Server에서 처리가 효율적
6. 추가
    - 톰캣(WAS)에는 아파치(웹서버)의 기능(웹서비스데몬, Httpd)를 포함하고 있다.
    - 일반적인 WAS, Web Server 구조가 아닌 걸로 알고 있음.
    - WAS, Web Server를 따로 두고 쓰는 이유가 성능때문이라고 하는 건 잘못되었다.

    톰캣5.5 이상부터는 httpd의 native모듈을 사용해서 정적파일을 처리하는 기능을 제공하는데 이것이 순수 아파치 Httpd만 사용하는 것과 비교해서 성능이 전혀 떨어지지 않기 때문이다.
    그럼에도 톰캣앞에 아파치를 두는 이유는 하나의 서버에서 php애플리케이션과 java애플리케이션을 함께 사용하거나, httpd 서버를 간단한 로드밸런싱을 위해서 사용해야 할 때 필요하기 때문.


    "자원 이용의 효율성, 장애 극복, 유지보수의 편의성을 위해 분리"

    Web Server를 WAS 앞단에 두고 WAS들을 플러그인 형태로 설정하면 더욱 효율적인 분산처리가 가능.

     

     

## Web Service Architecture

다양한 구조를 가질수 있다.

1. Client - Web Server - DB
2. Client - WAS - DB
3. Client - Web Server - WAS - DB

![https://gmlwjd9405.github.io/images/web/web-service-architecture.png](https://gmlwjd9405.github.io/images/web/web-service-architecture.png)

3번 구조 동작과정

1. Web Server는 웹 브라우저 클라이언트로 부터 HTTP 요청을 받는다.
2. Web Server는 클라이언트 요청(Request)를 WAS에 보낸다.
3. WAS는 관련된 Servlet을 메모리에 올린다.
4. WAS는 web.xml을 참조하여 해당 Servlet에 대한 Thread를 생성한다.(Thread Pool 이용)
5. HttpServletRequest와 HttpServletResponse 객체를 생성하여 Servlet에 전달
    - Thread는 Servlet의 service()메서드를 호출
    - service() 메서드는 요청에 맞게 doGet() or doPost() 메서드 호출
    - protected doGet(HttpServletRequest request, HttpServletResponse response)
6. doGet() doPost() 메서드는 인자에 맞게 생성된 적절한 동적 페이지를 Response 객체에 담아 WAS에 전달한다.
7. WAS는 Response 객체를 HttpResponse 형태로 바꾸어 Web Server에 전달한다.
8. 생성된 Thread를 종료하고, HttpServletRequest와 HttpServletResponse객체를 제거한다.

References

- [https://gmlwjd9405.github.io/2018/10/27/webserver-vs-was.html](https://gmlwjd9405.github.io/2018/10/27/webserver-vs-was.html)
- [https://jeong-pro.tistory.com/84#recentComments](https://jeong-pro.tistory.com/84#recentComments)