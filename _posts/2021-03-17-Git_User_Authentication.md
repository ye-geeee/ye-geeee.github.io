---
layout: post
title: Git User Authentication
---

![vscodeClone](/assets/img/21-03-17/03_vscodeClone.png)

VSCode에서 `clone repositor` 를 했더니 인증을 위해 github으로 리다이렉팅 되더니 로그인을 하였다.  
그래서 나도 모르게 github 계정이랑 지금 워크스페이스랑 연동이 되었나보다! 했는데 웬걸...  
실명이 버젓이 들어가 있는게 아닌가ㅠㅠㅠㅠㅠㅠㅠ  

![githubError](/assets/img/21-03-17/04_githubError.png)

노트북을 새로 사서 (맥북 M1 칩 샀다 호호) 귀찮아서 git global setting 도 안해줬는데 이게 화근이 됐나보다. 빨리 다른 것도 하고 출근해야 하는데ㅠㅠㅠ 귀찮아라..  
Github 계정이 아닌 사람도 push할 수 있다는 사실에 1차 놀랍고, 2차로 내 실명을 데리고 온 것도 놀랍다.  
그래서 노트북 세팅할 겸 github 계정 추가하는 글을 쓴다.  
git은 보통 한 PC로 한 계정을 쓰므로 필자는 global로 설정을 해주었다.  

아래 command를 통해 git global config를 수정한다.

```bash
git config --global user.name username
git config --global user.email useremail
```

![gitsetting](/assets/img/21-03-17/05_gitsetting.png)

oh my zsh는 또 왜 깨지는거야..  
이제 정상적으로 내 계정으로 push가 된다. 
