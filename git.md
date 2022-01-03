# git

- git: 소스코드를 효과적으로 관리하기 위해 개발된 분산형 버전 관리 시스템
- 원격 저장소(Remote Repository): 파일이 원격 저장소 전용 서버에서 관리되며 여러 사람이 함께 공유하기 위한 저장소
- 로컬 저장소(Local Repository): 내 PC에 파일이 저장되는 개인 전용 저장소

![img](https://blog.kakaocdn.net/dn/dcc3ub/btqNQamP35o/hmXwFIBPB82ea5NX3ZwQyK/tfile.svg)

- git add: stage에 올리기

- git commit: stage에 있는 것을 local repository에 올리기

- git push: local repository에 있는 것을 remote repository에 올리기

- git pull: remote repository에 있는 것을 local repository에 가져오기

- git reset: stage에 올린 것을 취소하기(과거의 버전으로 돌아가기)

  

### git 명령어

- 저장소 복사

  git clone 주소

- git에 대한 정보 등록하기

  git config --global user.name "이름"

  git config --global user.email "이메일"

- 등록한 정보 확인하기

  git config --list

- 버전에 포함시킬 파일 등록하기

  git add 파일명

  git add .

- 상태 확인하기

  git status

- 커밋

  git commit -m "메세지"

- 푸쉬

  git push origin 브랜치명
  
  

# 브랜치(branch)

- 브랜치: 독립적으로 어떤 작업을 진행하기 위한 개념, 다른 사람의 작업에 영향을 받지 않고 독립적으로 특정 작업을 수행 가능하다.

### 브랜치

통합 브랜치: 언제든지 배포할 수 있는 버전을 만들 수 있어야 하는 브랜치

- 모든 기능이 작동하는 안정적인 상태를 유지해야 한다.

토픽 브랜치: 기능 추가나 버그 수정과 같은 단위 작업을 위한 브랜치

### 브랜치 전환하기

- 체크아웃(checkout): 체크아웃을 실행하여 작업하고자 하는 브랜치로 전환할 수 있다. 전환한 브랜치는 HEAD가 된다.

- HEAD: 현재 사용 중인 브랜치의 선두 부분

  ![image-20211231112548604](C:\Users\gkgpa\AppData\Roaming\Typora\typora-user-images\image-20211231112548604.png)

~(틸드, 물결기호): 몇 세대 앞의 커밋 지정

^(캐럿, 삽입기호): 몇 번째 원본인지

- 커밋하지 않은 변경 내용이 있는 채로 브랜치를 전환하면, 그 변경 내용은 전환된 브랜치에서 커밋할 수 있다. 이때, 그 내용이 전환된 브랜치에서도 변경되었다면 체크아웃에 실패할 수 있다. stash를 이용하여 변경 내용을 일시적으로 다른 곳에 저장하여 충돌을 피한 후 체크아웃을 해야 한다.
- stash: 파일의 변경 내용을 일시적으로 기록해두는 영역



### 브랜치 병합

1. merge:  이 명령어에 병합할 커밋 이름을 넣어 실행하면, 지정한 커밋 내용이 HEAD가 가리키고 있는 브랜치에 넣어진다. 변경 이력이 모두 저장된다.

   git merge 브랜치명

2. rebase: commit 이력을 하나로 통합할 수 있다.

   git rebase 브랜치명


### 브랜치 명령어

- 브랜치 목록 보기

  git branch

- 브랜치 생성

  git branch 브랜치명

- 브랜치 삭제

  git branch -d

- 브랜치 전환

  git checkout 브랜치명

- 브랜치 생성 + 전환

  git checkout -b 브랜치명

# 원격 저장소

- pull(가져와 병합하기): 충돌이 없는 경우 자동적으로 병합 커밋이 만들어진다. 충돌이 있을 경우, 충돌난 부분을 수동으로 해결한 다음 직접 commit해야 한다.
- fetch(가져오기): 원격 저장소의 내용을 확인만 하고 병합은 하고 싶지 않은 경우에 사용한다.
- push(밀어넣기): 로컬 저장소에서 원격 저장소로 push할 때에는, push한 브랜치가 fast-forward 병합 방식으로 처리되도록 지정해야 한다.

# 태그(Tag)

태그: 커밋을 참조하기 쉽도록 알기 쉬운 이름을 붙이는 것

- 한 번 붙인 태그는 브랜치처럼 위치가 이동하지 않고 고정된다.

태그 종류

- 일반 태그(Lightweight tag): 이름만 붙일 수 있다.
- 주석 태그(Annotated tag): 이름, 태그에 대한 설명, 서명, 태그 생성자, 이메일, 날짜 정보를 포함시킬 수 있다.

### 태그 명령어

- 태그 추가: 현재 HEAD가 가리키고 있는 커밋에 태그를 추가

  git tag 태그명

- 주석 달린 태그 추가

  git tag -a 태그명

- 태그 목록 확인

  git tag -n

- 태그 정보를 포함한 이력 확인

  git log --decorate

- 태그 삭제

  git tag -d 태그명

# commit 변경하기

- 이전에 작성한 커밋 수정하기: --amend 옵션
- 이전에 작성한 커밋 지우기: revert 명령어
- 필요 없어진 커밋 버리기: reset
- 다른 브랜치로부터 특정 커밋을 가져와서 내 브랜치에 넣기: cherry-pick
- 커밋 이력 편집하기: rebase -i
- 브랜치 상의 커밋을 모아 하나로 병합하기: merge --squash