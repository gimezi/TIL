# Git

###  Git이란?
- Git = 분산 버전관리 시스템 (중간중간 수정한 것들도 모두 저장이 됨)
- 지금까지 온 과정을 파악할 수 있고, 이전 버전과 비교도 가능함
- 코드의 '변경 이력' 기록 + '협업'


### Git의 영역

1. Working Directory : 실제 작업 중인 파일들이 위치하는 영역
2. Staging Area : Working Directory에서 변경된 파일 중, 다음 버전에 포함시킬 파일들을 선택적으로 추가, 제외할 수 있는 중간 준비 영역
3. Repository : 버전(commit) 이력과 파일들이 영구적으로 저장되는 영역, 모든 버전과 변경 이력이 기록됨.

- commit(버전): 변경된 파일들을 저장하는 행위
- Working Directory --**(add)**-> Staging Area--**(commit)**-> Reposity


### Git 문법
- ***git init*** : 로컬 저장소 설정(초기화), 시작할 때
- ***git add 파일명*** : 변경사항이 있는 파일을 staging area에 추가
- ***git commit -m "내용"*** : staging area에 있는 파일들을 저장소로 보냄(commit을 생성하고 변경이력을 남김)
- ***git config --global user.email "(내 주소)"***
- ***git config -- global user.name "(내이름)"*** : commit 작성자 설정(한번만 해줘도 됨)
- ***git log*** : commit 했던 것들 확인가능
  

# GitHub
   
### GitHub란? 
- GitHub = 원격저장소
- 코드와 버전 관리 이력을 온라인 상의 특정위치에 저장하여 여러 개발자가 협업하고 공유할 수 있는 저장공간
- 위에서 만든 commit를 올릴 수 있다

### GitHub 이용하기(push)
1. [GitHub](https://github.com/) 가입하기
2. 새로운 repository 만들기
   - start a new repository
   - 이름 입력
   - public 설정
   - create a new repository
3. 만들어진 repository 주소 복사 해놓기
4. ***git remote add 별명 주소*** : 로컬 저장소에 원격 저장소 추가
5. ***git remote -v*** : 추가되었는지 확인
6. 추가하려고 하는 파일을 git을 이용해 우선 commit까지 완료함
7. ***git **push** -u 별명 master*** : 원격저장소에 commit 목록을 업로드 (오류 뜰때는 master -> +master으로 수정하면 가능)
8. 원격 저장소에 잘 되었나 확인하기!
9.  현재 로컬 저장소에서 원격 저장소를 삭제하고 싶다면 ***git remote rm 별명***


### GitHub에서 파일 가져오기(pull, clone)
1. ***git **pull** 별명 master*** : 원격저장소의 변경사항을 가져옴(업데이트)
2. ***git **clone** 주소*** : 원격 저장소 전체를 복제해서 다운로드 받아옴
- 아무것도 없는 상태에서 **처음**받는거면 clone, 이후에 변경사항이 생겨서 **업데이트**가 필요하면 pull

### gitignore
- 공유하지 않을 파일을 추적하지 못하도록 설정하는데 사용하는 파일
- a.txt를 공유하고 싶지 않을 경우,
  - ***echo a.txt >> .gitignore***
  - 이미 git의 관리를 받으면 적용 X