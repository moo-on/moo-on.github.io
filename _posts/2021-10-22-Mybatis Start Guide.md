---
date: 2021-10-22

title: "Mybatis Start Guide"
excerpt: "about the Mybatis"

categories: Java
tags: java, jdbc, sql

toc: true  
toc_sticky: true
toc_label: "contents"
toc_icon : 

last_modified_at : 2021-10-22
---

## Mybatis란?
![image](https://user-images.githubusercontent.com/70089259/138476296-ad67fba4-a5d7-4074-a18e-af02c5248898.png)



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

미리 메모리에 connection을 만들어 놓는 것이 mybatis의 취지



[reference]  
[https://mybatis.org/mybatis-3/ko/getting-started.html](https://mybatis.org/mybatis-3/ko/getting-started.html)
