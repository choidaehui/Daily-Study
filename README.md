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
     
     
    


