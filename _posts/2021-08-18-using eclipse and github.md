---
date: 2021-08-18

title: "Eclipse integrate with Github"
excerpt: "about the eclipse and Github"

categories: DevTool
tags: eclipse, github

toc: true  
toc_sticky: true
toc_label: "contents"
toc_icon : 

last_modified_at : 2021-08-18
---

eclipse와 원격 저장소의 연결 방법은 크게 2가지이고 후자의 방법을 추천한다.

## 1. eclipse에서 github와 연결하기
- clone해오기(git reposit 자동생성)
- 직접 git reposit 만들어서 커밋하기

이 말이 이해가 안 갈수가 있다.  
local에서 eclipse-workspace와 git repository라는 폴더 2개에서 eclipse-workspace에서 작업을 하고 git repository폴더에 올리는 식이다. GUI를 지원을 하지만 컴팩트한 환경이 아니기에 과감히 포기.  
**+eclipse 연결할 때 따로 github에서 토큰을 발행 후 인증을 해줘야하는 것으로 바뀌었다.아무것도 모르고 이메일과 비밀번호를 입력 칸에 넣는다면 git-receive-pack not permitted on 라는 에러문구가 보일것이다.**

## 2. workspace에서 gitbash 이용하기
이 방법이 가장 간단하지만, 현재 github에서 remote해서 연결을 할 때 자동 생성되는 branch는 main이다. 그리고 git bash에서 자동 설정되어있는 branch는 master이다.
가장 깔끔하게 integrate하는 방법을 소개해보자면,  
1. git pull origin main :보통 ignore파일을 만들어놓는게 편하니 해당 명령어로 불러온다. (해당 명령어로 불러오면 git bash에서는 자동으로 master branch가 생성되면서 저장된다.)
2. git add .
3. git commit -m "하고싶은말"
4. git push -u origin master
이렇게 하면 github에는 master branch가 새로 생성되고 main branch가 default로 그대로 남아있을 것이다.
5. main branch를 setting에 들어가서 master branch에 default를 넘겨주고 삭제해준다.

혹은
1. git pull --rebase origin main으로 받아오면 master branch가 생성이 안되고 main branch가 생성되면서 받아와지게 된다. 
2. git checkout main으로 master에서 main으로 바꿔주면된다.
 - 개인적으로 해당 방법보다 위에 방법이 더 나은거 같다.

초기 세팅 완료다.
역시 jetbrain이 좋다. Pycharm 쓸 때는 local_repo, remote_repo 촥 펼쳐서 클릭 몇 번으로 진행했는데.. 이클립스에 비해 개발환경 파일 설정도 훨씬 편하것 같고... 유튜브프리미엄 결제 할 돈 아껴서 intellij&pycharm 구독을 해야겠다.