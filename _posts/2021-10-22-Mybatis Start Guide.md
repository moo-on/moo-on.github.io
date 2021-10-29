---
date: 2021-10-22

title: "Mybatis Guide"
excerpt: "about the Mybatis"

categories: Java
tags: java, jdbc

toc: true  
toc_sticky: true
toc_label: "contents"
toc_icon : 

last_modified_at : 2021-10-22
---

* JDBC를 모른다면, 아래 링크를 보고와주세요.  
<https://moo-on.github.io/java/JDBC-Start-Guide/>


## Mybatis란?
![image](https://user-images.githubusercontent.com/70089259/138476296-ad67fba4-a5d7-4074-a18e-af02c5248898.png)

DB access을 더 쉽게 도와주는 개발 프레임워크이다.  
JDBC로 DB에 access에 하는 작업을 캡슐화하며, 일반SQL쿼리, 저장프로시져 및 고급 매핑을 지원하며 모든 JDBC코드 및 매개변수의 중복 작업을 제거합니다.  

디자인적으로도 SQL쿼리들을 분리해 한 곳에 모아두어 분리 시킬 수 있습니다.

JDBC의 단점(중요코드 노출, 개발속도, 자바소스&SQL소스 혼합)을 극복.  


---

## 기본 환경 구성 & 사용법 

![image](https://user-images.githubusercontent.com/70089259/138473652-23875d3d-0d61-46f3-a40e-4388b6504a3b.png)

* 기본 모듈이 아니기에, Mybatis jar파일을 다운로드 후에 lib폴더 안에 넣어줘야 한다.

Mybatis를 사용하려면 위에 보이는 3가지 파일이 존재해야한다.

1. configuration XML : 환경파일 구성 2,3번 파일을 1번 파일에 연결 시켜야 함. 
    - config.xml코드
        
        ```xml
        <?xml version='1.0' encoding='UTF-8'?>
        <!DOCTYPE configuration
                PUBLIC "-//mybatis.org//DTD Config 3.0//EN"
                "http://mybatis.org/dtd/mybatis-3-config.dtd">
        <configuration>
            <properties resource = "com/web/mybatis/db.properties"/>
            <environments default="development">
                <environment id="development">
                    <transactionManager type="JDBC"/>
                    <dataSource type="POOLED">
                        <property name="driver" value="${driver}"/>
                        <property name="url" value="${url}"/>
                        <property name="username" value="${username}"/>
                        <property name="password" value="${password}"/>
                    </dataSource>
                </environment>
            </environments>
            <mappers>
                <mapper resource="com/web/mybatis/memberMapper.xml"/>
            </mappers>
        </configuration>
        ```
        
        1. properties resource 재설정
        2. properties파일 과 키값이 일치해야함(jdbc 연결 post 참조)
        3. mapper resource 재설정
          
2. properties 파일
    - db.properties코드
        
        ```
        driver=com.mysql.jdbc.Driver
        url=jdbc:mysql://localhost:3306/test
        username=root
        password=1234
        ```
        
3. SQL 문장을 저장해놓은(Mapper파일, XML)
    - Mapper.xml
        
        ```xml
        <?xml version="1.0" encoding="UTF-8" ?>
        <!DOCTYPE mapper
          PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
          "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
        <!--namespace는 맘대로 중복파일 방지용, but 일반적으로 폴더위치명 -->
        <mapper namespace="com.web.mybatis.memberMapper
          SQL구문이 들어감
        </mapper>
        ```
        

 mybatis api가 1번 xml파일을 읽고 작동을 한다.

---

## SqlSessionFactory란?  
* JDBC를 모른다면, 아래 링크를 보고와주세요.  
<https://moo-on.github.io/java/JDBC-Start-Guide/>

![image](https://user-images.githubusercontent.com/70089259/138480692-407a2a64-ef30-4662-936a-8ab480df8063.png)

JDBC의 경우 DB와 access할 경우 connection객체의 생성과 작업 완료 후 닫어주는 방법으로 매번 연결 객체 생성과 종료가 반복된다. 이로 인해 리소스가 많이 들어가게 된다.  
[link참고](https://github.com/moo-on/jsp-tutorial/blob/MVC4/src/com/web/model/MemberDAO.java/)


Mybatis의 경우 
1. SqlSessionFactory를 만들어준 후 이 안에 Sqlsession 5-8개를 생성을 해준다. 
2. 각각의 sqlsession은 DB와의 연결을 끊지 않고 연결이 필요한 메소드마다 session을 하나씩 가져가서 사용 후 반납을 한다. 기존에 DB와 연결하고 끊고를 하면서 사용했던 리소스가 줄어든다.


소스코드를 통해서 어떻게 사용되는지 확인하고싶다면 아래 링크를 참고하세요. 

factory생성_link참고  
<https://github.com/moo-on/jsp-tutorial/blob/master/src/com/web/model/MemberDAO.java>

SQLmapping_link참고  
<https://github.com/moo-on/jsp-tutorial/blob/master/src/com/web/mybatis/MemberMapper.xml>

 
---
[reference]  
- [https://mybatis.org/mybatis-3/ko/getting-started.html](https://mybatis.org/mybatis-3/ko/getting-started.html)