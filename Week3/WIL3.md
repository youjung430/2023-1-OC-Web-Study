# 3차시 (3/28)

## Git Branch

개발을 하다 보면 코드를 여러 개로 복사해야 하는 일이 자주 생긴다. 코드를 통째로 복사하고 나서 원래 코드와는 상관없이 독립적으로 개발을 진행할 수 있는데,  이렇게 독립적으로 개발하는 것이 브랜치다. 즉 브랜치는 여러 개발자들이 동시에 각자 독립적인 작업 영역 안에서 마음대로 소스코드를 변경하고, 분리된 작업 영역에서 변경된 내용을 나중에 원래의 버전과 비교해서 하나의 새로운 버전으로 만들어 낼 수 있게 해준다.

Branch 의 실체는 포인터. 가장 마지막 커밋을 가리키는 포인터이다.

![Untitled](https://git-scm.com/book/en/v2/images/two-branches.png)

`$git branch testing` 명령어를 통해 testing 브랜치를 만든다. testing 브랜치는 지금 작업하고 있던 마지막 커밋을 가리킨다.

![Untitled](https://git-scm.com/book/en/v2/images/head-to-master.png)

Git에 있는 특수한 포인터 ‘HEAD’는 지금 작업 중인 로컬 브랜치를 가리킨다. testing 브랜치를 새로 만들었지만 Git은 아직 master 브랜치를 가리키고 있다. `git branch` 명령은 브랜치를 만들기만 하고 옮기지는 않는다.

![Untitled](https://git-scm.com/book/en/v2/images/head-to-testing.png)

`$git checkout testing` 명령을 통해 testing 브랜치로 이동할 수 있다. HEAD가 testing 브랜치를 가리킨다.

![Untitled](https://git-scm.com/book/en/v2/images/advance-testing.png)

새로 커밋을 하면 testing 브랜치는 앞으로 이동한다. 그러나 master 브랜치는 여전히 이전 커밋을 가리킨다. 

![Untitled](https://git-scm.com/book/en/v2/images/checkout-master.png)

`$git checkout master` 명령을 통해 master 브랜치가 가리키는 커밋을 HEAD가 가리키게 하고, 워킹 디렉토리의 파일도 그 시점으로 되돌려 놓았다. 앞으로 커밋을 하면 다른 브랜치의 작업들과 별개로 진행되므로 testing 브랜치에서 임시로 작업하고 master 브랜치로 돌아와 하던 일을 계속 할 수 있다.


## Git 3-ways merge

![Untitled](https://git-scm.com/book/en/v2/images/basic-merging-1.png)

3-ways merge를 위해서는 각 브랜치가 가리키는 커밋 두 개와 공통 조상 하나가 필요하다.

### 3-ways merge가 효율적인 이유

공통 조상 C2 커밋의 A라는 부분을 C4는 그대로 두고, C5는 A’로 변경했다고 가정하자. 공통 조상 커밋이 없고 C4와 C5만 있다면 merge할 때 A가 원래 A였는지 A’였는지 정하기가 어렵다. 따라서 충돌 여부도 알 수가 없다. 하지만 ****공통 조상 커밋이 있다면 기준점을 두고 어떤 점이 변경되었는지 쉽게 살펴볼 수 있다.

### Conflict

C4와 C5 둘 다 A 부분을 변경한상태에서 merge한다면 conflict가 발생한다. 이때는 개발자가 둘 중에 받아들일 것 (current change vs incoming change) 을 직접 선택해야 한다.

## Git-flow

![Untitled](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbEkY05%2FbtrpU1NDIEz%2FztBJisDxZgsKFAuXVUBAbK%2Fimg.png)

master는 기준이 되는 브랜치로, 제품을 배포하는 브랜치이다. develop 브랜치는 master에서 만들어지고, 상시로 버그를 수정한 커밋들이 추가된다. 새로운 기능 추가 작업이 있는 경우 develop 브랜치에서 feature 브랜치를 생성하여 작업하고, 작업이 완료되면 develop 브랜치로 merge 된다. 모든 기능이 완료되면 develop 브랜치를 release 브랜치로 보내 QA(품질검사)를 하며 보완한다. 배포를 했는데 미처 발견하지 못한 버그가 있을 경우 hotfixes 브랜치에서 수정한다.

## 커밋 메시지 컨벤션

commit message에 대한 약속. 동료 개발자 혹은 미래의 자신에게 변경사항을 전달하는데 도움을 준다. 제목, 본문, 꼬리말 세가지 파트로 나뉜다.

type : subject

body

footer

### Commit Type

`Feat`: 새로운 기능 추가

`Fix`: 버그 수정

`Design`: CSS등 사용자 UI 변경

`Docs`: 문서 수정

`Style`: 코드 포맷팅, 세미콜론 누락, 코드 변경이 없는 경우

`Refactor`: 코드 리펙토링

`Test`: 테스트 추가나 수정

`Chore`: 여러가지 production code와 무관한 부분

### Subject

제목은 최대 50글자가 넘지 않도록 하고 마침표 및 특수 기호는 사용하지 않는다. 개조식 구문으로 작성한다.

### Body

무엇을 변경했는지 또는 왜 변경했는지를 상세히 적는다.

### Footer

`유형: #이슈 번호` 형식으로 사용한다.

`Fixes`: 이슈 수정중 (아직 해결x)

`Resolves`: 이슈 해결

`Ref`: 참고할 이슈가 있을 때

`Related to`: 해당 커밋에 관련된 이슈 번호 (아직 해결 x)

## 느낀점

단순히 프로그래밍 언어 문법, 알고리즘을 배우는 것이 아닌 git을 사용해 다른사람과 협업하는 법이나 git에 대한 정확한 개념 등 개발자로서의 기본을 배울 수 있어서 뜻깊다. 3-ways-merge와 2-ways-merge 의 차이점에 대해 더 공부해보고 싶다.