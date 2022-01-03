# Git - 발전편

​	이 문서에서는 브랜치를 다뤄 보고자한다.

## branch(브랜치)

​	프로젝트를 진행할 때 동일한 소스코드 위에서 서로 다른작업을 할 수 있게 만들어 주는 기능이다. 정확하게는 독립적으로 어떤 작업을 진행하기 위한 개념이다. 필요에 의해 만들어지는 각각의 브랜치는 다른 브랜치의 영향을 받지 않기 때문에, 여러 작업을 동시에 진행할 수 있다.

- 통합 브랜치(Integration Branch) : 언제든지 배포할 수 있는 버전을 만들 수 있어야 하는 브랜치이다.

  > 보통 main 브랜치를 사용

- 토픽 브랜치(Topic Branch) : 기능 추가, 버그 수정과 같은 단위 작업을 위한 브랜치이다.

  > 각각의 독립된 작업을 수행할 수 있는 브랜치

## Checkout

​	체크아웃 이라는 명령어를 실행하여 원하는 브랜치에서 작업을 진행 할 수 있다.

> git checkout 브랜치이름

- HEAD : 현재 사용중인 브랜치의 선두를 나타냄

![image-20220103161522401](C:\Users\audtj\AppData\Roaming\Typora\typora-user-images\image-20220103161522401.png)

## Stash

​	커밋하지 않은 변경내용이나 새롭게 추가한 팔이 인덱스와 작업 트리에 남아 있는 채로 다른 브랜치로 전환(checkout)하면, 그 변경 내용은 기존 브랜치가 아닌 전환된 브랜치에서 커밋할 수 있다.

> 단, 커밋 가능한 변경 내용 중에 전환된 브랜치에서도 한 차례 변경이 되어 있는 경우에는 체크아웃에 실패할 수 있다. 이 경우 이전 브랜치에서 커밋하지 않은 변경 내용을 커밋하거나, stash를 이용해 일시적으로 변경내용을 다른 곳에 저장하여 충돌을 피하게 한 뒤 체크아웃을 해야한다.

​	Stash 란, 파일의 변경 내용을 일시적으로 기록해두는 영역이다. 작업트리와 인덱스 내에서 아직 커밋하지 않은 변경을 일시적으로 저장 가능하다. 이 내용은 나중에 다시 불러와서 원하는 브랜치에서 커밋할 수 있다.

![image-20220103162017307](C:\Users\audtj\AppData\Roaming\Typora\typora-user-images\image-20220103162017307.png)

## 브랜치 통합

- merge : 여러 개의 브랜치를 하나로 모을 수 있다.

  - fast-foward : 단순히 main 브랜치를 이동 시켜서 병합

  ![image-20220103163948648](C:\Users\audtj\AppData\Roaming\Typora\typora-user-images\image-20220103163948648.png)

  > master(main) 에 브랜치를 합치고 싶으면 HEAD가 master에 있어야한다.  아래는 merge후 결과 이다.

  ![image-20220103164001920](C:\Users\audtj\AppData\Roaming\Typora\typora-user-images\image-20220103164001920.png)

  > git merge bugfix
  >
  > 를 master 브랜치에서 입력하면된다.

  - non fast-foward

  ![image-20220103163931751](C:\Users\audtj\AppData\Roaming\Typora\typora-user-images\image-20220103163931751.png)

  > D에서 bugfix를 merge 해주면 결과가 위와 같다.

  **merge후 충돌이 있으면 충돌을 처리한 후에 새롭게 커밋을 해줘야한다.**

  충돌이 없는 경우는 자동으로 커밋을 해준다.

  

- rebase : 브랜치를 하나로 합치는 다른 방법.

  - git rebase master(main) : 합칠 브랜치에서 실행

  - git rebase --continue : 충돌 이후 계속 진행 할려면 사용

  - git rebase --abort : rebase자체를 취소함

    

  > rebase 라는게 re + base로 브랜치의 base를 새로 만든다는 의미인것 같다.

  ![image-20220103164041400](C:\Users\audtj\AppData\Roaming\Typora\typora-user-images\image-20220103164041400.png)

![image-20220103164103519](C:\Users\audtj\AppData\Roaming\Typora\typora-user-images\image-20220103164103519.png)

> rebase는 merge와 반대로 병합될 branch에서 실행한다.

![image-20220103164115463](C:\Users\audtj\AppData\Roaming\Typora\typora-user-images\image-20220103164115463.png)

> 마무리는 fast-foward  병합을 한다.
>
> git merge bugfix     ## (in master)



## Tag

태그란, 커밋을 참조하기 쉽게 이름을 붙인 것

- 일반 태그(Lightweight tag) : git tag <tagename>, git tag, git log --decorate
  - 이름
- 주석 태그(Annotated tag) : git tag -a <tagname>, git tag -n
  - 이름
  - 설명
  - 서명
  - 이 태그를 만든 사람의 이름, 이메일, 만든 날짜

> 보통 릴리스 브랜치에서는 주석 태그를 사용한다. 일반 태그는 토픽 브랜치에서!

- 삭제 : git tag -d <tagename>



## Commit 변경

- 이전에 작성한 커밋 수정하기 : git commit --amend

  >  현재 커밋에 새로 내용을 추가 또는 수정

- 이전에 작성한 커밋 지우기 : git revert <commit>

  > 이걸 하고 나면 revert 했다는 커밋이 생겨남

- 커밋을 버리고 특정 버전으로 다시 되돌아가기 : git reset --hard, soft, mixed <commit>

  > reset 전의 커밋은 ORIG_HEAD 라는 이름으로 참조 가능
  >
  > 실수한 경우 ORIG_HEAD로 reset하면 된다.

| 모드명 | HEAD의 위치 | 인덱스 | 작업 트리 |
| :----: | :---------: | :----: | :-------: |
|  soft  |    변경O    | 변경X  |   변경X   |
| mixed  |    변경O    | 변경O  |   변경X   |
|  hard  |    변경O    | 변경O  |   변경O   |



- 다른 브랜치로부터 특정 커밋을 가져와서 내 브랜치에 넣기 : git cherry-pick <commit>

  > 충돌이 있을 경우 충돌 처리후 커밋

- 커밋 이력 편집하기 : git rebase -i

  - pick -> squash : 통합
  - pick -> edit : 수정

- 브랜치 상의 커밋을 하나로 모아 병합하기 : git merge --squash

  ![image-20220103172916060](C:\Users\audtj\AppData\Roaming\Typora\typora-user-images\image-20220103172916060.png)

  

  