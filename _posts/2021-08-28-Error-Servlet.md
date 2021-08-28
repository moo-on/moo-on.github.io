---
date: 2021-08-28

title: "Error-Servlet"
excerpt: "about the Servlet error"

categories: Error
tags: eclipse, servlet, tomcat

toc: true  
toc_sticky: true
toc_label: "contents"
toc_icon : 

last_modified_at : 2021-08-28
---


## java.lang.classnotfoundexception: com.mysql.jdbc.driver  

eclipse에 tomcat연동해서 MySQL에 데이터 넣는 중에, 해당 에러가 떴다. jdbc driver를 못 찾길래, 
1. jdk lib안에 jar파일의 드라이버를 넣어주기.
2. preference에서 class path 추가해주기
3. project - properties 에서 build path에 해당 class path추가해주기  
 까지 한 후 똑같이 작업을 하였지만, 밑의 에러가 발견

## javax.servlet.servletexception: not insert  

완벽하게 참조를해주었지만, 해당 에러가 뜨길래, eclipse 환경 내 문제가 아닌것 같길래 tomcat-lib안에 다시 jdbc driver를 넣어준 후 해결 완료.

> **why?** servlet파일들은 tomcat안 에서 모든 것을 해결하기에 에러가 발생한 것 같다.  
**add** tomcat-lib 안에 jar파일을 넣어줌에도 에러가 발생한다면, tomcat내부에서 lib을 찾을수있게 xml파일을 건들어보는것도 해결방법 중 하나일것 같다.