---
layout: post
title: Git Commit Message Template
---

# What is Commit Message?

## How can I check the commit message?

Git에서 수정사항을 반영할 때에는 commit message를 작성하게 되어있다. 이전에 작성한 commit message를 통해 본 프로젝트에서 반영된 추가, 수정, 삭제에 대한 이력을 확인할 수 있다. 해당 프로젝트에 어떤 수정 사항이 포함되었는지 확인할 때 사용한다. 

```shell
git log [--oneline] [--author username] [--before [date]
```
위의 command를 사용하면 이전에 작성한 commit message를 확인할 수 있다. 
- `git log` : 이전에 작성한 commit message를 확인할 수 있다. 옵션이 없을 경우, 메세지의 전체 내용을 보여준다.
- `--oneline` : 대표 commit 내용만 확인할 수 있다.
- `--author` : 사용자별로 commit message를 필터링할 수 있다.
- `--before` : 보고싶은 commit message의 범위를 필터링할 수 있다.
## Why we need good commit message?
좋은 commit message를 남기는 것은 협업과 히스토리를 기록하는 데에 중요하다. 통일화되지 않은 commit message를 읽는 것은 수정 내용을 파악하는 데에 시간이 더 걸린다. message rule을 지정해놓으면 규칙에 따라서 수정 사항의 내용을 파악하는 데에 시간을 단축시킬 수 있고 결과적으로 유지보수하기 쉬운 프로젝트를 구성하는데 도움이 된다.
# Message Rule
## What we have to consider?
commit message에는 세 가지 부분을 고려해야 한다.
- Style : Markup syntax, wrap margins, grammar, capitalization, punctuation(따옴) 을 고려하고 가능한한 단순하게 작성한다.
- Content : 어떤 내용을 포함하고 어떤 내용을 포함하면 안될지 고려한다.
- Metadata : issueID와 PR을 트래킹한다.
## Good Commit Message Rule
아래는 보고 있던 블로그에서 가져온 정보인데, 링크를 클릭하면 원본 블로그에서 자세한 설명을 볼 수 있다.
1. [Separate subject from body with a blank](https://chris.beams.io/posts/git-commit/#separate)
2. [Limit the subject line to 50 characters](https://chris.beams.io/posts/git-commit/#limit-50)
3. [Capitalize the subject line](https://chris.beams.io/posts/git-commit/#capitalize)
4. [Do not end the subject line with a period](https://chris.beams.io/posts/git-commit/#end)
5. [Use the imperative mood in the subject line](https://chris.beams.io/posts/git-commit/#imperative)
6. [Wrap the body at 72 characters](https://chris.beams.io/posts/git-commit/#wrap-72)
7. [Use the body to explain *what* and *why* vs. *how*](https://chris.beams.io/posts/git-commit/#why-not-how)
## Let's make template!
git commit message는 보통 아래와 같은 형식으로 작성하는 것 같다.
```bash
# <type> : <Subject>
# <content>
# <issue track number>
```
subject와 같은 경우에는 `git log --oneline` 에서 보기 쉽게 50자를 넘지 않는 것이 좋고, content의 경우에도 72자를 넘어가지 않는 것을 권장한다.
그리고 이제 프로젝트에 맞게 type을 지정해야 하는데, 필자가 필요하다고 생각되는 type은 아래와 같다.
- feat : 새로운  Feature가 추가
- fix : 버그 수정
- refactor : 기존 코드를 refactoring
- docs : document 수정 사항
- style : 비즈니스 로직에는 수정이 없으나 코드 스타일이 변경
- test : test code를 추가하거나 수정
- build : 빌드 스크립트 수정
- ci : ci 구성 파일 및 스크립트 변경
- chore : 기타 수정 사항
이 내용으로 commit message template를 작성하면 아래와 같다.
```bash
# <type>: <subject>
##### Maximum length of subject is 50 ############## -> |
# content
######## Maximum length of content is 72 ########### -> |
# issue track number (#number)
# --- COMMIT END ---
# <type> list
#   feat    : New feature
#   fix     : Fix bug
#   refactor: Refactor code
#   style   : Change style of code(white space, semicolon etc)
#   test    : Add/Change/Delete test case
#   docs    : Add/Change/Delete document
#   build   : Change in build script
#   ci      : Change in ci script
#   chore   : etc
# ------------------
#     Capitalize the subject line
#     Use imperitive mood in subject
#     Do not use period at the end of subject
#     Seperate subject and content with a blank line
#     Use the body explain "what" and "why" vs "how"
#     Use "-" when content contains multiline
# ------------------
```
이제 열심히 써봐야지 호호
# Setting Template
작성한 Git Message Template을 적용하는 방법은 다음 순서이다.
1. Git message template을 작성한다.
2. 아래 command로 `.gitconfig` 파일을 수정한다.
    ```bash
    git config commit.template [template 파일]
    ```
![gitconfig](/assets/img/21-03-17/01_gitconfig.png)
3. 그 다음부터는 아래 이미지처럼 `git commit` 을 했을 경우, 작성한 template읋 확인할 수 있다. 
![gitconfig](/assets/img/21-03-17/02_gitcommit.png)
다른 git config와 동일하게 commit template 또한 global과 repository로 범위를 설정할 수 있다. 
1. git global에다가 commit template을 설정하는 방법
    필자는 global config 경로가 `~/.gitconfig` 로 설정되어 있었다. 아래 command를사용하면 `~/.gitconfig` 파일을 수정할 수 있다.
    ```bash
    git config --global commit.template [template 파일]
    ```
2. 작업 중인 repository에 commit template을 지정하는 방법
    프로젝트를 git을 통해 형상관리를 하고 있었다면 프로젝트 내에 `.git` 디렉토리가 생성되었을 것이다. 
    Repository의 root directory에서 아래 command를 사용하면 `path/to/project/.git/config` 파일에 설정 파일이 저장된다.
    ```bash
    git config commit.template [template 파일]
    ```
# Reference
[https://chris.beams.io/posts/git-commit/](https://chris.beams.io/posts/git-commit/)
[https://blog.ull.im/engineering/2019/03/10/logs-on-git.html](https://blog.ull.im/engineering/2019/03/10/logs-on-git.html)
[https://junwoo45.github.io/2020-02-06-commit_template/](https://junwoo45.github.io/2020-02-06-commit_template/)
[https://medium.com/humanscape-tech/효율적인-commit-message-작성을-위한-conventional-commits-ae885898e754](https://medium.com/humanscape-tech/%ED%9A%A8%EC%9C%A8%EC%A0%81%EC%9D%B8-commit-message-%EC%9E%91%EC%84%B1%EC%9D%84-%EC%9C%84%ED%95%9C-conventional-commits-ae885898e754)
[http://karma-runner.github.io/0.10/dev/git-commit-msg.html](http://karma-runner.github.io/0.10/dev/git-commit-msg.html)