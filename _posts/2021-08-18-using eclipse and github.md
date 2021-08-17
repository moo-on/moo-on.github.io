---
date: 2021-08-18

title: "Eclipse integrate with Github"
excerpt: "about the eclipse and Github"

categories: Error
tags: eclipse, github

toc: true  
toc_sticky: true
toc_label: "contents"
toc_icon : 

last_modified_at : 2021-08-18
---

eclipse와 원격 저장소의 연결 방법은

## 1. eclipse에서 github와 연결하기
- clone해오기(git reposit 자동생성)
- 직접 git reposit 만들어서 커밋하기

이 말이 이해가 안 갈수가 있다.  
local에서 eclipse-workspace와 git repository라는 폴더 2개에서 eclipse-workspace에서 작업을 하고 git repository폴더에 올리는 식이다. GUI를 지원을 하지만 미니멀한 환경이 아니면 안쓰고 만다 라는 생각을 하고있는 나였기에 과감히 포기.  
**+eclipse 연결할 때 따로 github에서 토큰을 발행 후 인증을 해줘야하는 것으로 바뀌었다.아무것도 모르고 이메일과 비밀번호를 입력 칸에 넣는다면 git-receive-pack not permitted on 라는 에러문구가 보일것이다.**

## 2. workspace에서 gitbash 이용하기
이 방법이 가장 간단하지만, 현재 github에서 remote해서 연결을 할 때 자동 생성되는 branch는 main이다. 그리고 git bash에서 자동 설정되어있는 branch는 master이다.
가장 깔끔하게 integrate하는 방법을 소개해보자면,  
1. git pull origin main :보통 ignore파일을 만들어놓는게 편하니 해당 명령어로 불러온다.
2. 해당 명령어로 불러오면 git bash에서는 자동으로 master branch가 생성되면서 저장된다.
    -  이게 싫으면, 
    -  git pull --rebase origin main으로 받아오면 master branch가 생성이 안되고 main branch가 생성되면서 해당 branch에 받아와지게 된다. 
    -  그 후 git checkout main으로 master에서 main으로 바꿔줘야되는데 번거로우니까 그냥 12345번 따라하자.
3. git add .
4. git commit -m "하고싶은말"
5. git push -u origin master
이렇게 하면 github에는 master branch가 새로 생성되고 main branch가 default로 그대로 남아있을 것이다.
6. main branch를 setting에 들어가서 master branch에 default를 넘겨주고 삭제해준다.

초기 세팅 완료다.
역시 jetbrain이 짱이다.협업 할 때도 import시 개인 개발환경에 따른 파일 설정도 훨씬 편하다. 유튜브프리미엄 결제 할 돈 아껴서 intellij&pycharm 구독을 하자.