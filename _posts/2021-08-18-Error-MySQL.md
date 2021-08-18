---
date: 2021-08-18

title: "Error-MySQL"
excerpt: "about the MySQL error"

categories: Error
tags: MySQL

toc: true  
toc_sticky: true
toc_label: "contents"
toc_icon : 

last_modified_at : 2021-08-18
---

## Could not acquire management access for administration
>solution  

1. 실행 console
2. services.msc
3. MySQL 찾아서 수동으로 실행 시켜주기  

+8.026 최신 버전에서는 connection상태에서도 Workbench는 런타임 에러가 있으니 좀 더 낮은 버전으로 하는 것을 추천.

---
## Mysql Workbench : current profile has no WMI enabled
> solution  

mysql workbench의 버그이므로 단순하게 재접속하면 풀린다.
