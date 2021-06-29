# daily-Study
HTML, CSS, Javascript

# git & github 정리

## 기본적인 명령어

cmder.net -> 깃 터미널(windows용)
형식) git + 명령어 + -옵션

git config --global -e 
-> 깃 설정 파일 열기

gti config --globla user.name "DaeHui"
확인) git config user.name

git congfig --global core.autocrlf true 
-> 줄 바꿈 적용

git init
-> 깃 초기화
git -rf .git 
-> 깃 삭제

git status 
git config --global alias.st status 
git st
-> 단축키 만들기 예

1. git add a.txt
-> a.txt 파일을 staged files로 옮김 (깃이 트레킹 함)

2. git rm --cached * 
-> 모든 파일들이 unstaged files로 옮겨짐 (깃이 트래킹 하지 않음)

3. git add * 
-> 디렉토리의 모든 파일이 staged files로 옮겨짐

4. git add *.CSS
-> 디렉토리의 .CSS 파일만 staged files로 옮겨짐

5. echo *.log > .gitignore
-> .log 파일은 깃에서 트래킹 하지 않음

참고) ctrl + k
-> 터미널창 clear

6. git status -s 
-> 현재 상태 간단하게 확인

7. git diff
-> 파일 변경 사항을 비교할 때
   git diff --staged
   git diff --cached
-> staged files에 있는 파일들만 변경사항을 비교할 때

8. git config --global -e
   [diff]
   tool = vscode
   [difftool "vscode"]
   cmd = code --wait --diff $LOCAL $REMOTE
   git difftool
   git difftool --staged
-> vscode에서 파일들의 변경사항을 확인 가능

9. git commit
   git commit -m "second commit"
   
   git commit -am "third commit"
-> staged files와 unstaged files 모두 메시지와 함께 커밋
-> 커밋 메시지에 맞게 커밋 내용이 포함 되어야 함

10. git rm c.txt
-> 삭제된 c.txt파일이 staged files에 적용

11. git mv style.css f.css
-> 변경된 파일명이 staged files에 적용

12. head 
-> 현재 버전
    head~1 
-> 현재 이전 버전 (현재의 부모 버전)
    head~2
-> 현재 이전 이전 버전 (현재의 부모의 부모 버전)

13. git log -p 
-> 변경된 파일내용을 버전별로 확인

14. git checkout 328708d 
-> 해시코드의 버전으로 파일 이동
    git checkout fix 
-> fix 브랜치로 이동

15. git log --pretty=online
    git log --oneine --graph --all
-> 메인과 브랜치의 전체적인 변경사항을 확인
    git log -3 
-> 최근 커밋 중 3개만 확인
    git log --oneline -3 
    git log --author = "DaeHui"
    git log --before = "2020-09-08"
    git log --grep = "project"
-> 프로젝트에 포함된 커밋 확인
    git log HEAD
    git log HEAD~1
    git log HEAD~2
-> 해당 버전의 파일을 확인

16. git show 0ad2dbb
-> 해시코드에 해당하는 파일을 볼 수 있음

## tag 사용
-> tag별로 출시버전을 정해두면 사용하기 편함
예) v2.0.0 
주요 major기능 변경.minor기능 변경.기존의 fix기능에서 오류 수정, 기능 개선
사용법)
  1. git tag v1.0.0 + 해시코드
     git tag v1.0.1 + 해시코드 -am "release note"
     -> 태그에 메시지 남길 때 사용
     
  2. git show v1.0.1
     -> 태그에 해당하는 버전 파일을 확인 할 수 있음
  
  3. git tag
     -> 만들어진 모든 태그 확인 가능
   
  4. git tag -d v1.0.1
     -> 태그 삭제
     
  5. git checkout v1.0.1
     -> 태그에 해당하는 파일 확인
     
  6. git checkout -b testing v2.0.0
     -> v2.0.0 태그의 버전파일에 testing 브런치 생성
     
  7. git push origin v1.0.0 
     -> 서버에 해당 태그의 버전 파일을 올림
     git push orign --tags
     -> 모든 태그의 버전 파일들을 서버에 올림
     git push orign --delete v1.0.0
     -> 해당 태그의 파일을 삭제
     
## 브랜치(branch)
1. git branch 
-> 현재 컴퓨터에 있는 브랜치 확인
2. git branch --all 
-> 서버(깃 허브 등)에 있는 브랜치를 포함하여 모든 브랜치 확인
3. git branch new-branch
-> new-branch라는 브랜치 생성
4. git switch new-branch
-> new-branch라는 브랜치로 이동
5. git switch -c new-branch2
-> new-branch2라는 브랜치를 생성한 후 이동
6. git checkout 해시코드
-> 해시코드에 해당하는 버전의 파일로 이동
7. git checkout fix
-> fix라는 브랜치로 이동
8. git checkout -b testing
-> testing라는 브랜치 생성 후 이동
9. git branch --merged
-> 머지된 브랜치 확인
10. git merge fix
-> fix라는 브랜치를 머지
11. git branch -d new-branch2
-> new-branch2라는 브랜치를 삭제
12. git push orign --delete new-branch2 
-> 서버(깃 허브 등)에 있는 new-branch2라는 브랜치를 삭제
13. git branch --move fix fix-welcome 
-> fix라는 브랜치를 fix-welcome라는 브랜치로 이름을 변경
14. git push --set-upstream origin fix-welcome
-> 서버에 있는 브랜치 이름을 fix-welcome으로 변경
15. git log master..test
-> 마스터 브랜치와 테스트 브랜치 사이의 기록 확인
16. git diff master..test
-> 마스터 브랜치와 테스트 브랜치 사이의 변경 코드 확인

## 머지(merge)
### fast-forward merge
1. git merge feature-a
-> 마스터 브랜치에 feature-a 브랜치를 머지
-> 히스토리에 기록 되지 않음
2. git branch -d feature-a
-> 머지 후 feature-a 브랜치 삭제

### git merge --no-ff 
1. git merge --no-ff feature-c
-> 마스터 브랜치에 feature-c 브랜치를 머지
-> 히스토리에 기록 됨
2. git branch -d feature-c
-> 머지 후 feature-c 브랜치 삭제

### three-way merge
1. git merge feature-b
-> 마스터 브랜치에서 feature-b 브랜치를 생성한 후 마스터 브랜치에서 커밋이 발생한 경우
feature-b브랜치와 동시에 묶어주는 머지커밋이 만들어 짐

### merge conflict
1. 수동방법
git merge feature
-> 마스터 브랜치와 feature 브랜치의 파일 수정 내용이 같을 경우에 merge conflict 발생
git merge --abort
-> 머지 한 것을 취소
open main.txt
-> 파일을 수동으로 수정(HEAD 문자열과 feature문자열을 삭제)
git add main.txt
git merge --continue
-> 수정된 파일 내용이 머지 됨

2. vscode방법
git config --global -e
-> 에디트 창 열기
[merge]
tool = vscode
[mergetool "vscode"]
cmd = code --wait $MERGED 
-> 에디트 창에 추가
git config --global mergetool.keepbackup false
-> .orig 충돌된 원본 파일을 저장하지 않도록 설정
git merge feature
-> 머지충돌 발생
git mergetool 
-> 수정할 파일의 옵션에서 선택
git merge --continue 

## 리베이스(rebase)
-> three-way merge 상황에서 다른 개발자와 협업 하지 않고 나의 로컬에 있는 작업만 머지할 경우
마스터 브랜치의 최신 버전과 rebase를 이용하여 fast-forward merge가 가능

1. git checkout feature-b
-> feature-b 브랜치로 이동
2. feature-b> git rebase master
-> feature-b 브랜치를 마스터 브랜치에  rebase 함
3. git checkout master
-> 마스터 브랜치로 이동
4. master> git merge feature-b 
-> feature-b 브랜치를 마스터 브랜치에 머지(히스토리 기록 없음)
-> fast-forward merge 임

### rebase --onto
-> 브랜치(예 profile)에서 파생된 브랜치(예 profile-ui)를 마스터 브랜치에 머지 할 때 사용

1. master> git rebase --onto master profile profile-ui
-> 마스터 브랜치에 profile-ui 브랜치를 rebase함
2. master> git merge profile-ui
-> 마스터 브랜치에 profile-ui 브랜치를 머지 함

### cherry pick
-> 브랜치에서 특정한 커밋 부분만 마스터 브랜치에 머지 할 때

1. master> git cherry-pick f2bq1n8(해당 해시코드)
-> 마스터 브랜치로 해당 커밋 부분이 이동
     
     
    


