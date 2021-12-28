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

  

# git의 명령어

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

# git branch

- branch: 독립적으로 어떤 작업을 진행하기 위한 개념, 다른 사람의 작업에 영향을 받지 않고 독립적으로 특정 작업을 수행 가능

  

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