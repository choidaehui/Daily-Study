# dailyStudy
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

## cherry pick
-> 브랜치에서 특정한 커밋 부분만 마스터 브랜치에 머지 할 때

1. master> git cherry-pick f2bq1n8(해당 해시코드)
-> 마스터 브랜치로 해당 커밋 부분이 이동

## stash stack
-> 커밋하기 전 파일들을 임시저장하여 코드에 오류가 있는지 확인

1. git stash push
   git stash push -m "first try"
-> git에서 트래킹하지 않는 unstaged files을 스태시 하지 않음
2. git stash -u 
-> git에서 트래팅하지 않는 unstaged files을 스태시 함
3. git stash list
-> 전체적인 스태시 목록 확인
4. git stash show stash@{3}
-> 해당 아이디 스태시 파일의 수정된 내용 확인
5. git stash apply stash@{1}
-> 해당 스태시 파일의 목록을 유지하면서 나의 워킹디렉토리에 적용
6. git stash pop stash@{1}
-> 해당 스태시 파일의 목록이 없어지고 나의 워킹디렉토리에 적용
7. git stash drop stash@{1}
-> 해당 스태시 파일 삭제
8. git stash clear
-> 전체 스태시 파일들 삭제
9. git stash branch newbranch
-> newbranch라는 브랜치를 만들어서 스태시 파일들을 저장
     
 # Javascript 정리
 ## 제어문
 1. if(true) {
      document.write("if문의 조건을 만족하여 문장이 실행");
      }
 -> 웹 브라우저 화면에 문장이 나타남
    if(false) {
      document.write("if문의 조건을 만족하여 문장이 실행");
      }
 -> 웹 브라우저 화면에 문장이 나타나지 않음
 2. if...else문
    var number = prompt("숫자를 입력하세요.");
    if(number>0) {
      alert("0이상의 수를 입력하세요.");
      }
    else {
      document.write("입력한 숫자: "+number);
      }
 3. 조건 연산자
    var score = 85;
    (score > 75)? alert("통과") : alert("실패");
 -> 조건이 true이면 "통과" false이면 "실패"
 ## falsy -> false로 인정하는 값
 1. 0
 2. ""
 3. NAN(not a number) -> 값을 할당하지 않고 연산할 경우
 4. undefined -> 값이 처음부터 변수에 할당되지 않음
 5. null -> 유효하지 않은 값
 ## 3의 배수 검사기
 1. var userNumber = prompt("숫자를 입력하세요.");
    if (userNumber != null) {.....}
    else {....}
 -> true가 될 경우가 많은 조건을 if문에 넣고 다른 조건은 else문에서 처리
 2. var userNumber = prompt("숫자를 입력하세요.");
    var displayArea = document.queryselector('#result');
    if(userNumber != null) {
      if(userNumber % 3 === 0) {
         displayArea.innerHTML = userNumber + "은 3의 배수 입니다.";
         }
      else {
         displayArea.innerHTML = userNumber + "은 3의 배수가 아닙니다.";
         }
      }
  -> <div id = "result"></div> 영역에 3의 배수인지 아닌지 확인한 후 결과값 표시   
  ## switch문
  -> 여러 조건 값 확인할 때 사용
  1. var session = prompt("관심 분야를 선택해주세요. 1-마케팅, 2-개발, 3-디자인","1")
  -> 기본 값으로 "1"지정
  switch(session) {
      case "1" : document.write("201호 강의실 입니다.")
         break;
      case "2" : document.write("202호 강의실 입니다.")
         break;
      case "3" : document.write("203호 강의실 입니다.")
         break;
      default: alert("잘못입력했습니다.");
      }
  -> 콜론 다음에 둘 이상의 명령을 실행한다면 중괄호 {   }로 묶음
  -> 사용자가 입력한 값이 조건값과 일치하지 않을 때 실행할 명령은 default: 에 넣는다
 ## for문
 1. 1부터 100까지 더하는 for문
 var sum = 0;
 for(var i = 1; i < 101; i++) {
      sum += i;
   }
 ## for문 중첩사용(구구단)
 1. for(var i = 2; i<=9; i++) {
      document.write(i+"단");
      for(var j=1; j<=9; j++) {
         document.write(i+"*"+j+"="+i*j+"<br>");
         }
     }
 ## while문 사용(팩토리얼 계산기)
 1. var i = 0
    while(i<10) {
      document.write('반복조건이 true이면 반복합니다.<br>');
      i += 1;
      }
 2. var i = 0
    do {
         document.write('반복조건이 true이면 반복합니다.<br>');
         i +=1;
         } 
    while(i<10);
 3. var n = prompt("숫자를 입력하세요.");
    var nFact = 1;
    var i = 2;
    while(i <= n) {
     nFact *= i;
     i++;
     }
    document.write(n+"i="+nFact);
 
 ## 반복문,continue문, if문 활용(10까지 짝수 더하기 프로그램)
 1. var n = 10;
    var sum = 0;
    
    for(var i = 0; i <=n; i++) {
     if(i % 2 === 1) {
      continue;
      -> 반복문장을 건너뛰고 반복문의 맨 앞으로 돌아감
      }
      sum += i;
      document.write(i+"---------------"+sum+"<br>");
    }
    
  ## 변수
  1. 표기법
  birthYear, currentYear
  -> 첫번째 단어는 소문자, 두번째 단어부터는 대문자로 시작
  -> 낙타표기법(camel case)
  -> 변수 이름의 첫 글자는 반드시 문자나 _(밑줄), $(달러)기호로 시작
  2. 템플릿 문자열      
  -> const originPrice = 24500;    
  -> document.queryselector("#showResult").innerHTML = '원래 가격은 ${originPrice}원 입니다.';
  
  ## 변수를 선언할 때 사용
  1. let      
  -> 재선언 불가      
  -> 재할당 가능    
  예)if(true) {   
      >>let a = 10;     
      >>let a = 15; -> 사용불가   
      >>a = 5; -> 사용가능   
      >>}   
      console.log(a); -> 접근불가    
  2. const   
  -> 재선언 불가     
  -> 재할당 불가   
  -> 상수처럼 사용하고 처음 선언시 반드시 값을 대입   
  >예)if(true) {   
  >>const a= 10;    
  >>const a = 15; -> 사용불가      
  >>      a = 5; -> 사용불가   
  >>      }      
  >console.log(a); -> 접근불가   
  
  
      
  
  
  
    
      
 
  
  
    
 
    
    


