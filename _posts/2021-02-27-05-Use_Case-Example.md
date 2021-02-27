---
layout: post
title: Use Case Example
---

해당 내용은 글 작성자 마음대로 작성한 것입니다. 따라서, 부정확한 내용이 있을 수 있습니다.

## Use Case 도출

이제 만들고 싶은 서비스의 사용자 인증 기능 Use Case Diagram을 작성해보자.

사용자 인증 기능에는 크게 회원가입, 로그인, 그리고 계정 정보 조회가 있다. 그리고 계정 정보 조회에는 ID 조회,  비밀번호 조회가 있다.

## Use Case 작성하기

1. 해당 시스템에 관여하는 외부 환경은 사용자 뿐이기 때문에 사용자로 `actor`를 하나 생성한다.
2. 해당 시스템에 대한 명세를 하기 위해 `rectangle` 을 통해 서비스 scope을 만들어준다.
3. 해당 시스템의 scope안에 들어갈 생각해두었던 `usecase`를 작성한다.
4. `uscase` 의 relation을 정의한다.
    - 사용자가 실질적으로 사용하는 서비스는 `actor` 에서 `usecase` 로 relation을 정희한다.
    - 사용자가 실제 사용하는 ID 조회, 비밀번호 조회는 계정 정보 조회의 한 부분이므로 `generalization` 을 사용한다.

위와 같이 수행했을 때, 결과적으로 나오는 Use Case Diagram은 아래와 같다.

```bash
@startuml authenticaion

skinparam actorStyle awesome
left to right direction

actor 사용자 as US

rectangle Authentication {
usecase "회원 가입" as UC1
usecase "로그인" as UC2
usecase "계정 정보 찾기" as UC3
usecase "ID 찾기" as UC4
usecase "PWD 찾기" as UC5

US --> UC1
US --> UC2
US --> UC4
US --> UC5

UC4 --|> UC3
UC5 --|> UC3

```

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7c3f0b55-ebc9-47ec-8cfa-edb07407ad20/01_Authentication.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7c3f0b55-ebc9-47ec-8cfa-edb07407ad20/01_Authentication.png)

## Use Case Description

 아래는 위의 `usecase` 중 회원 가입에 대한 명세서이다. 해당  `usecase` 에서 일어나기 전에 필요한 사전 조건, 사후 조건 그리고 일어날 수 있는 장애를 미리 예상해서 시스템 개발을 구체적으로 구상해보는 것이 좋은 것 같다.

|Category|Description|
|---|---|
|Use Case|회원 가입|
|Actor|사용자|
|개요|사용자는 해당 시스템을 이용하기 위해 회원가입을 진행해야 한다.|
|사전 조건|- Database 연결 상태에 이상이 없다.|
|사후 조건|- 가입한 사용자 정보는 데이터베이스에 저장된다.
|기본 흐름|1. 사용자가 해당 시스템에 접속한다.<br/> 2. 사용자가 로그인 화면이 뜬다.<br/>3. 사용자는 회원가입 버튼을 누른다.<br/>4. 사용자는 개인 정보를 입력한다.<br/>5. 사용자는 회원 가입 버튼을 누른다.|
|대체 흐름|4a. 사용자의 계정 정보가 이미 있는 경우, 이미 계정 정보가 있다는 팝업과 함께 해당 UseCase를 종료한다.|

관련해서 Use Case 자료들은 [깃헙링크](https://github.com/ye-geeee/moni-app-server/tree/develop/diagram)에 계속해서 업데이트 할 예정이다.
