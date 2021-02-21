---
layout: post
title: PlantUML Use Case Diagram
---

## Use Case Diagram  개요

이제 Plugin을 설치하였으니 다이어그램을 작성해보자. PlantUML 파일의 확장자는 `.puml` 이다. 해당 확장자를 가진 파일을 하나 생성하자.  

제일 먼저 Use Case Diagram을 작성해볼 것이다. 

From Wiki
유스 케이스 다이어그램(use case diagram)은 사용자, 그리고 사용자가 수반한 다른 유스 케이스 간의 관계를 보여주는 사용자-시스템 간 상호작용의 표현이다. 유스 케이스 다이어그램은 각기 다른 종류의 시스템 사용자와 각기 다른 유스 케이스를 식별할 수 있으며 다른 유형의 다이어그램이 수반되기도 한다. 유스 케이스는 원이나 타원으로 표현된다.

Use case diagram의 예시는 다음과 같다.

![https://upload.wikimedia.org/wikipedia/commons/thumb/1/1d/Use_case_restaurant_model.svg/800px-Use_case_restaurant_model.svg.png](https://upload.wikimedia.org/wikipedia/commons/thumb/1/1d/Use_case_restaurant_model.svg/800px-Use_case_restaurant_model.svg.png)

구성 요소를 보면 타원, 화살표, 실선, 사람, 그리고 시스템 바운더리가 있다. 구체적으로 구성요소와 표현하고자 하는 바가 무엇인지 알아보자.

## Use Case

UseCase 다이어그램에서 UseCase는 사용자의 요구사항을 뜻한다. 다이어그램에서 UseCase는 타원으로 표현한다. PlantUML에서 UseCase를 그리는 방법은 괄호`()` 를 이용하는 방법과 `usecase` 라는 키워드를 사용할 수 있다. 아래와 같이 `as [keyword]` 라는 것은 별칭을 정하는 것으로 추후에 관계를 정의할 때 사용이 된다.

```go
@startuml

(UC1)
usecase UC2
usecase UseCase3 as UC3
(UseCase4) as (UC4)

@enduml
```

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/20fc3c1e-7047-44af-a855-054d2d1596bf/01_UseCaseDiagram.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/20fc3c1e-7047-44af-a855-054d2d1596bf/01_UseCaseDiagram.png)

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

## Actor

UseCase다이어그램에서 Actor는 구현 대상이 아니라 시스템과 상호작용하는 외부 환경이라고 생각하면 된다. 

Actors는 `::` 를 사용하거나 `actor` 키워드를 사용한다.  UseCase와 마찬가지로 `as [keyword]` 로 별칭을 정해 추후에 관계를 정의할 때 사용할 수 있다.

```go
@startuml

:Actor1:
:Actor2: as AT2
actor Actor3
actor :Actor4: as AT4

@enduml
```

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/90af140c-1000-4e27-8bef-90400b940c9b/02_UseCaseActor.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/90af140c-1000-4e27-8bef-90400b940c9b/02_UseCaseActor.png)

PlantUML은 Actor의 style을 변경할 수 있도록 지원해준다. style은 아래 코드와 같이 awesome과 Hollow등을 지원하니 참고하자. 

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a31fb390-1d27-4344-9e39-7ba2565ce8ac/03_UseCaseActorAwesome.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a31fb390-1d27-4344-9e39-7ba2565ce8ac/03_UseCaseActorAwesome.png)

### 참고 링크

[https://plantuml.com/ko/use-case-diagram](https://plantuml.com/ko/use-case-diagram)
[https://gnaseel.tistory.com/22](https://gnaseel.tistory.com/22)