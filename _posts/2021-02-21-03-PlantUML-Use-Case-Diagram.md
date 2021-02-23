---
layout: post
title: PlantUML Use Case Diagram
---

[Pre-condition](#pre-condition)

[System](#system)

[Actor](#actor)

[UseCase](#use-case)

[Relation](#relation)

프로젝트를 위해 작성할 Diagram 중에서 제일 먼저 Use Case Diagram을 작성해볼 것이다. 위키를 보면 Use Case Diagram에 대한 설명이 아래와 같이 나와있다.

From Wiki
유스 케이스 다이어그램(use case diagram)은 사용자, 그리고 사용자가 수반한 다른 유스 케이스 간의 관계를 보여주는 사용자-시스템 간 상호작용의 표현이다. 유스 케이스 다이어그램은 각기 다른 종류의 시스템 사용자와 각기 다른 유스 케이스를 식별할 수 있으며 다른 유형의 다이어그램이 수반되기도 한다. 유스 케이스는 원이나 타원으로 표현된다.

Use case diagram의 예시는 다음과 같다.

![000_UseCaseExample](https://upload.wikimedia.org/wikipedia/commons/thumb/1/1d/Use_case_restaurant_model.svg/800px-Use_case_restaurant_model.svg.png)

구성 요소를 보면 시스템 바운더리, 타원, 사람, 그리고 선 들이 있다. 이 선들이 바로 Use Case Diagram의 구성요소들으로 `System`, `Actor`, `Use Case`, `Relation` 이라고 명칭한다.  본 포스터에서 Use Case Diagram의 구성요소에 대한 이해와 그리는 방법, 그리고 실제 PlantUML에서 작성하는 문법을 알아보자.  

# Pre-condition

이전 포스터에서 IntelliJ에 PlantUML Plugin을 적용하는 방법을 알아보았다.

이제 Plugin을 설치하였으니 다이어그램을 작성해보자. PlantUML 파일의 확장자는 `.puml` 이다. 해당 확장자를 가진 파일을 하나 생성하자.

아래와 같이 Diagram이 잘 그려지면 성공한 것이다.

![00_PreCondition.png](/assets/img/21-02-21/00_PreCondition.png)

# System

`System`은 개발하고자 하는 시스템을 뜻한다. Diagram 상에서는 Use Case를 둘러싸고 있는 네모난 사각형으로 표현한다.

### PlantUML - System

System을 표현하는 방법

- `rectangle`

rectangle을 사용하면 큰 네모 박스가 생성된다. 해당 박스 안에 Use Case를 작성하면 된다.

```bash
@startuml

rectangle Restaurant {
    usecase "Eat Food" as UC1
}

@enduml
```

![01_System.png](/assets/img/21-02-21/01_System.png)

# Actor

Use Case Diagram 샘플에서 사람 모양으로 볼 수 있는 아이콘은 `Actor`이다. Actor는 구현 대상이 아니라 시스템과 상호작용하는 외부 환경이라고 생각하면 된다. 예를 들어, 시스템 기능을 사용하는 사람, 시스템에 정보를 제공하는 또 다른 시스템 등이 있다.

### PlantUML - Actor

Actor를 표현하는 두 가지 방법

- `:[Actor name]:`
- `actor [Actor name]`

`as [keyword]` 로 별칭을 정해 추후에 관계를 정의할 때 사용할 수 있다.

```go
@startuml

:Actor1:
:Actor2: as AT2
actor Actor3
actor :Actor4: as AT4

@enduml
```

![02_Actor.png](/assets/img/21-02-21/02_Actor.png)

PlantUML은 Actor의 style을 변경할 수 있도록 지원해준다. style은 아래 코드와 같이 awesome과 Hollow등을 지원하니 참고하자. 

![03_ActorAwesome.png](/assets/img/21-02-21/03_ActorAwesome.png)

# Use Case

`UseCase`는 시스템이 사용자에게 제공해야하는 요구사항을 뜻한다. 다이어그램에서 UseCase는 타원으로 표현한다.

### PlantUML - Use Case

`UseCase` 를 작성하는 두 가지 방법

- `( )`
- `usecase`

`as [keyword]` 로 별칭을 정해 추후에 관계를 정의할 때 사용할 수 있다.

```go
@startuml

(UC1)
usecase UC2
usecase UseCase3 as UC3
(UseCase4) as (UC4)

@enduml
```

![04_UseCase.png](/assets/img/21-02-21/04_UseCase.png)

Use Case를 작성할 때에 들어갈 내용이 많을 경우, `--`, `==`, `..`  선을 통해 추가로 많은 description을 작성할 수 있다.

```bash
@startuml

usecase UC1 as "You can use
several lines to define your usecase.
You can also use separators.
--
Several separators are possible.
==
And you can add titles:
..Conclusion..
This allows large description."

@enduml
```

![05_UseCaseDescription.png](/assets/img/21-02-21/05_UseCaseDescription.png)

# Relation

`Actor` 와 `UseCase` 사이의 `Relation`을 정의한다. 종류는 연관(Association), 의존(Dependency), 일반화(Generalization)이 있다.

## Association

`Actor` 가 수행하는 동작은 보통 Association으로 표현한다.

### PlantUML - Association

- `Relation`는 `->` 과 같이 화살표로 표현한다.
- Diagram 상 더 긴 화살표를 그리고 싶을 때는 `-` 의 길이를 더 늘린다. (ex. `-->`)
- `Relation` 정의 후에 `:` 마크를 통해 Label을 작성할 수 있다.

예제를 따라하다보면, `-` 가 하나인 화살표의 경우, 오른쪽에 생성이 되고 의 길이가 길어지면 같은 선상이 아닌 아래와 위에 작성하게 되는 것으로 보인다. 

```bash
@startuml

actor User as User1
User1 -> (start)
User1 --> (write post) : This is Label
User1 ---> (post content) : This is Label2

@enduml
```

![06_Association.png](/assets/img/21-02-21/06_Association.png)

## Dependency - Include

`Dependency` 는 `UseCase` 사이에서의 관계 혹은 `Actor` 사이에서의 관계를 정의할 때 사용된다. 관계에는 `extend` 와 `include` 가 있다.

Include(포함 관계)는 한 `UseCase` 가 다른 `UseCase` 실행을 전제로 할 때 사용이 된다. 포함하는 `UseCase` 에서 포함되는 `UseCase` 로 화살표가 향하고, 화살표는 점선으로 <<include>>  태그가 붙는다.

예를 들면 "글쓰기" 기능은 항상 "로그인"이 선행되어야 한다. 이는 UseCase Diagram으로 아래와 같이 표현할 수 있다.

![07_IncludeExample.png](/assets/img/21-02-21/07_IncludeExample.png)

### PlantUML - Include

- 점선으로 표시해야하기 때문에 `.>` 기호를 사용
- <<include>> 태그는 lable로 작성 가능

```bash
@startuml

usecase "포함하는 UseCase" as UC1
usecase "포함되는 UseCase" as UC2
UC1 .> UC2 : <<include>>

@enduml
```

![08_Include.png](/assets/img/21-02-21/08_Include.png)

## Dependency - Extend

Extend(확장 관계)는 확장 기능 `UseCase`와 확장 대상 `UseCase`에서 사용된다. 확장 기능 `UseCase` 에서 확장 대상 `UseCase` 로 화살표가 향하고, 화살표는 점선으로 <<extend>> 태그가 붙는다.

예를 들면, "파일 첨부하기" 기능은 "글쓰기" 기능을 확장한다. UseCase Diagram으로 표현하면 아래와 같다.

![09_ExtendExample.png](/assets/img/21-02-21/09_ExtendExample.png)

### PlantUML - Extend

- 점선으로 표시해야하기 때문에 `.>` 기호를 사용
- <<extend>> 태그는 lable로 작성 가능

```bash
@startuml

usecase "글쓰기" as UC1
usecase "파일 첨부하기" as UC2
UC1 <. UC2 : <<extend>>

@enduml
```

![10_Extend.png](/assets/img/21-02-21/10_Extend.png)

## Generalization

Generalization(일반화)는 유사한 `UseCase` 나 `Actor` 의 이해도를 높이기 위해 추상화 시키는 것을 뜻한다. 구체적인 `UseCase` 에서 추상적인 `UseCase` 방향으로 화살표가 향하고, 화살표는 실선으로 화살표의 끝은 삼각형으로 표현한다.

![11_GeneralizationExample.png](/assets/img/21-02-21/11_GeneralizationExample.png)

### PlantUML  - Generalization

- 실선이기 때문에 선은 `-` 로 표현
- 화살표를 삼각형으로 작성해야 하기 때문에 `-|>` 사용

```bash
@startuml

usecase "추상화 UseCase" as UC1
usecase "구체적인 UseCase" as UC2
UC1 <|- UC2

@enduml
```

![12_Generalization.png](/assets/img/21-02-21/12_Generalization.png)

## PlantUML에서 화살표 방향 전환

`UseCase` 사이에 화살표를 작성할 때에 화살표의 방향 전환이 필요할 때가 있다.

화살표 방향을 반대로 할 때에는 화살표 방향을 반대로 작성해주면 된다.

- 오른쪽 방향 화살표 : `->`
- 왼쪽 방향 화살표 : `<-`

```bash
@startuml

:user: -> (dummyLeft)
(dummyRight) <- :user:

@enduml
```

![13_ArrowReverse.png](/assets/img/21-02-21/13_ArrowReverse.png)

 이 외에도 화살표 방향을 네 방향으로 작성할 수 있다.

- 오른쪽 방향 화살표 : `-right->`
- 왼쪽 방향 화살표: `-left->`
- 위쪽 방향 화살표: `-up->`
- 아래쪽 방향 화살표: `-down->`

```bash
@startuml
:user: -left-> (dummyLeft)
:user: -right-> (dummyRight)
:user: -up-> (dummyUp)
:user: -down-> (dummyDown)
@enduml
```

![14_Arrow4Direction.png](/assets/img/21-02-21/14_Arrow4Direction.png)

자, 이렇게 Use Case Diagram에서 구성요소, 각자가 의미하는 바와 PlantUML에서 해당 구성요소를 어떻게 표현하는지 알아보았다. 다음 post에서는 실제 만들려고 하는 시스템을 기준으로 Use Case Diagram을 작성해보도록 하자.

# 참고 링크

[https://plantuml.com/ko/use-case-diagram](https://plantuml.com/ko/use-case-diagram)

[https://gnaseel.tistory.com/22](https://gnaseel.tistory.com/22)

[https://googry.tistory.com/2](https://googry.tistory.com/2)