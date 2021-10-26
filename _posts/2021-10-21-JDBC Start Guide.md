---
date: 2021-10-21

title: "JDBC Guide"
excerpt: "about the JDBC Start Guide"

categories: Java
tags: java, JDBC

toc: true  
toc_sticky: true
toc_label: "contents"
toc_icon : 

last_modified_at : 2021-10-21
---

# JDBC사용법  

![image](https://user-images.githubusercontent.com/70089259/138288823-336538a9-5ab7-4b00-aae7-bf648a619430.png)

## JDBC란?
다양한 DB들을 java언어 안에서 사용 할 수 있는 interface이다.
즉, DB측에서 JDBC interface의 형식으로 DB와 송신할 수 있는 api를 만드는 것이다.

## 구성환경
각 DB에서 connector를 배포하고 있다. tomcat 디렉토리 lib안에 넣어서 사용하면 된다.

## 기본 연결 객체

```java  
    private Connection conn;
    private PreparedStatement ps;
    private ResultSet rs;
```
위 3개의 객체가 DB와 커넥션을 해준다.


```java
//  데이터베이스 연결객체 생성
    public void getConnect() {
        String URL = "jdbc:mysql://localhost:3306/test";
        String user = "root";
        String password ="1234";

        // MySQL Driver Loading
        try {
            /*
            [정적로딩]
            DriverManager driver = new com.mysql.jdbc.Driver();
            conn = driver.getConnection(URL, user, password);
             
             
            [동적로딩]
            컴파일 시점에는 단순 문자열, 실행 지점에 
            Driver class를 메모리에 올림
            */
            Class.forName("com.mysql.jdbc.Driver");
            conn = DriverManager.getConnection(URL, user, password);
        } catch(Exception e) {
            e.printStackTrace();
        }
    }
```

URL, user, password는 DB설정과 똑같이 맞춰 준다.
만들어둔 getConnect() 메서드를 이용해서 DB의 변경이 이루어지는 메서드마다 호출해서 사용하면된다. 


Web 내부에서 JDBC를 통한 insert, delete, update 등 코드를 참고하고 싶다면, 아래 링크에서 확인 바랍니다.

[link](https://github.com/moo-on/jsp-tutorial/blob/MVC4/src/com/web/model/MemberDAO.java)