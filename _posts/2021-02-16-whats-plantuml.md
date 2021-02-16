---
layout: post
title: Introducing PlantUML
date:   2021-02-16 07:34:25
lastmod : 2021-02-17 03:51:33
sitemap :
  changefreq : daily
  priority : 1.0
---

**Wikipedia**
[PlantUML](https://plantuml.com/ko/)은 사용자가 플레인 텍스트 언어로부터 [UML](https://ko.wikipedia.org/wiki/%ED%86%B5%ED%95%A9_%EB%AA%A8%EB%8D%B8%EB%A7%81_%EC%96%B8%EC%96%B4) 다이어그램을 만들 수 있게 하는 오픈 소스 도구이다. PlantUML의 언어는 [도메인 특화 언어](https://ko.wikipedia.org/wiki/%EB%8F%84%EB%A9%94%EC%9D%B8_%ED%8A%B9%ED%99%94_%EC%96%B8%EC%96%B4)의 한 예이다. [Graphviz](https://ko.wikipedia.org/wiki/Graphviz) 소프트웨어를 사용하여 다이어그램을 배치한다.  

## PlantUML Page 탐구

PlantUML을 그냥 VSCode Extension으로 다운받아 사용해보려고 했는데, Paypal Donate을 보고 궁금해서 탐구를 시작했다. (프로젝트 하기 싫어서 그런 것 아님)

![PlantUML VSCode Readme](/assets/img/21-02-17_1.png)

PlantUML은 [Document Page](https://plantuml.com/ko/)가 따로 있어서 한 번 들어가 보았다. 생각보다 더 다양한 정보가 많은 사이트였는데, 한국어로도 지원을 해줘서 너무 기뻤다. 슬쩍 Sequence Diagram을 그리려고 PlantUML을 알아봤다가 생각보다 더 도움이 될 것 같아서 오늘 하루는 이 소프트웨어를 둘러보기로 하였다.  

우선, 페이지 이름이 믿음직스럽다. 마음에 든다.  

![PlantUML Document Page](/assets/img/21-02-17_2.png)

지원하는 다이어그램 외에도 생각보다 상당히 많은 다이어그램을 지원하고 있어서 놀랐다. 이번 프로젝트 설계할 때, 여기 있는 다이어그램을 다 사용해서 한 번 설계 비스무리한 것을 시도해봐야겠다.  

![PlantUML Diagram Category](/assets/img/21-02-17_3.png)

## PlantUML 사용하기

PlantUML은 기본적으로 jar 파일이고, GraphViz라는 소프트웨어와 함께 사용된다고 한다. 하지만, PlantUML Document 사이트에서 Online으로 작성할 수 있게 지원을 하고 있어서 급할 때는 온라인 서비스를 이용해도 좋을 것 같다.  

![PlantUML Online](/assets/img/21-02-17_4.png)

PlantUML이 적용되는 곳이 어디 있는지 확인을 해보았다. ([https://plantuml.com/ko/running](https://plantuml.com/ko/running)) 이미 Github, Gitlab 등 많은 Wiki에 적용하는 방법이 소개되어 있고, 웬만한 Editor에 Plugin이 모두 있다. 자기가 주로 사용하는 Editor에서 plugin을 설치하여 작성하면 될 것 같다.  

![PlantUML Running](/assets/img/21-02-17_5.png)

## IntelliJ PlantUML 적용하기

IntelliJ에서 Plugin으로 PlantUML을 설치한다. 아래와 같이 세 항목을 설치했다. 맨 위의 PlantUML integration만 있어도 되지만, 맞춤법도 틀리는 나에게 Syntax는 필수기기에 PlantUML Syntax Check을 설치해보았고, ERD를 그렸을 경우에 DDL로 변환해주는 Plugin까지 설치하였다. VSCode ERD Editor plugin과 동일한 기능이지 않을까 기대하면서 설치까지 완성하였다.  

![PlantUML IntelliJ](/assets/img/21-02-17_6.png)

### 참고 링크

[https://plantuml.com/ko/](https://plantuml.com/ko/)  
