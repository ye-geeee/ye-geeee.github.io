---
layout: post
title: Setting IntelliJ PlantUML
---

## Graphviz 설치

IntelliJ에서 드디어 다이어그램으로 그리려고 가장 기본적인 Use Case Diagram 문법을 사용해봤다. 잘 되는 것 같더니...  

![01_FirstUseCase](/assets/img/21-02-20/01_FirstUseCase.png)

다른 문법을 적용해서 다이어그램을 그리려 했더니 아래와 같이 에러가 발생한다. 어쩐지 뭔가 수월하다 했다.  

``` bash
Dot: Executable: /opt/local/bin/dot
File does not exist
Cannot find Graphviz. You should try... 
```

![02_GraphvizError](/assets/img/21-02-20/02_GraphvizError.png)

이전 포스트에서도 언급했듯이 PlantUML을 사용할 때는 Graphviz 소프트웨어를 사용한다. 그래서 Graphviz를 설치해줘야 한다. 필자는 Mac을 사용하고 있기 때문에 아래와 같이 Graphviz를 설치한다.  

``` bash
brew install libtool
brew link libtool
brew install graphviz
brew link --overwrite graphviz
```

자 이제 다시 IntelliJ를 실행시켜보자. 드디어 제대로 잘 나오는 것 같다.  

![03_GraphvizErrorFix](/assets/img/21-02-20/03_GraphvizErrorFix.png)

## IntelliJ에 Plugin 설치

IntelliJ에서 Plugins에 진입하기 위해서는 shift를 두번 눌러서 Plugins를 검색하여 진입하여도 되고, `IntelliJ Idea -> Preferences -> Plugins` 순서대로 진입한다.  

이전 포스트와 써놨듯이 필자는 아래 세 가지 plugin을 설치하였다.

1. PlantUML Integeration ← 무조건 설치
2. PlantUML Syntax Check ← 선택 사항
3. PlantUML2DDL ← 선택 사항

![04_IntelliJPlugin](/assets/img/21-02-20/04_IntelliJPlugin.png)

Plugin 설치 후에는 ide를 재시작한다.  
