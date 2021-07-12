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
  
  ## 함수   
  -> 특정 기능을 수행하는 소스코드를 따로 묶어놓은 덩어리   
  >function addNumber(){   
  >>var sum = 10+20;   
  >>console.log(sum);   
  >>}   
  >>->함수 선언   
  >>addNumber()   
  >>->함수 호출   
  
  ## 이벤트   
  -> 웹문서에서 버튼을 누르거나 이미지 위에 마우스 포인터를 올려놓는 등의 사건   
  예)1. add.html 파일 열기   
     2. <button onclick = "addNumber()">덧셈계산기</button>   
     3. add.js파일에 앞에 있는 addNumber()함수 소스를 작성하고 저장    
     4. add.html파일에 add.js파일을 연결   
     ><script src = "js/add.js"></script>   
     
  ## 매개변수와 인수   
  예) var num1 = paseInt(prompt("첫 번째 숫자는?"));   
  >   var num2 = paseInt(prompt("두 번째 숫자는?));   
  >   addNumber(num1, num2)   
  >   -> addNumber()함수의 num1, num2는 인수 = 전달인자 임    

  > function addNumber(a,b) {     
  > >var sum = a + b;   
  > >alert("두 수를 더한 값은 "+sum+"입니다.");   
  > >}   
  > >-> addNumber()함수의 a,b는 매개변수 = 인자 임   
      
  ## 매개변수 기본값 지정   
  예)function multiple(a, b=5, c= 10) {   
  >>return a*b+c;
  >}   
  >-> b=5, c=10로 기본값 지정   
  >multiple(5, 10, 20)   
  >->결과값은 70   
  >->a=5, b=10=, c=20   
  >multiple(10, 20)   
  >->결과값은 210   
  >->a=10, b=20, c=10   
  >multiple(30)   
  >->결과값은 160   
  >->a=30, b=5, c=10       

  ## return문 사용   
  -> 함수를 실행한 후 그 결과 값을 함수 밖으로 넘길 때 사용하고 반환위치는 함수를 호출한 위치   
  예) 1. var num1 = parseInt(prompt("첫 번째 숫자는?"));   
      2. var num2 = parseInt(prompt("두 번째 숫자는?"));    
      3. var result = 8. addNumber(num1, num2);   
      4. alert("두 수를 더한 값은 " +result+" 입니다.");   
      5. function addNumber(a,b) {    
      6.var sum = a + b;   
      7.return sum;
      }    
      실행순서:1->2->8->5->6->7->3->4   
      ---->6,7번을 return a + b;로 사용 가능     
          
  ## 변수의 적용범위   
  스코프(scope): 변수를 선언하고 사용할 때 변수가 적용되는 범위   
  지역변수=로컬변수: 한 함수 안에서만 사용할 수 있는 변수      
  전역변수=글로벌변수: 스크립트 소스 전체에서 사용할 수 있는 변수    
  예) var myVar = 100; -> 전역변수 선언    
  >test();    
  >document.write("myVar is"+myVar);   
  function test() {     
  >var myVar = 50; -> 지역변수 선언   
  >}   
  >->지역변수는 전역변수에 영향을 주지 않는다.   
  >->myVar의 값은 100   
  >->var myVar = 50이 myVar = 50일때는 전역변수가 되어 myVar의 값이 50이 된다.   
  블록변수: let예약어를 사용해 변수를 선언하고 변수를 선언한 블록 (중괄호({})로 묶은 부분)에서만 유효   
  익명함수: 함수 자체가 식이기 때문에 변수에 할당할 수 있고, 다른 함수의 매개변수로 사용가능     
  예)var add = function(a,b) {  
  >return a + b;   
  >>var sum = add(10, 20);  
  >>sum   
  >>->30   
  즉시 실행함수: 함수를 정의함과 동시에 실행하는 함수고 소스 끝에 세미콜론(;)을 붙임   
  예)(function() {   
  ......     
  })();   
  >(function() {    
  ......     
  }());    
  ->변수에 할당할 수 있고, 함수에서 반환하는 값을 변수에 할당할 수 있음   
  예)var result = (function(a,b) {   
  >return a + b;   
  >}(10,20));   
  console.log(result);   
  -> 30      
         
  ## 함수의 화살표 표기법(ES6버전부터)   
  > var hi = function() {     
  >> return "안녕하세요?";   
  >> }   
  > hi();   
  >= let hi = () => "안녕하세요?";   

  > var greet = function(name) {     
  >> return name+" 님, 안녕하세요?";
  > greet("경희");
  > = let greet = name => '${name}님, 안녕하세요?';   
  > greet("경희");   
      
  > var add = function(a, b) {    
  >> return a + b;   
  >> }   
  > add(10, 20)   
  > = let add = (a, b) => a + b;   
  > add(10, 20)     
     
  ## 이벤트 다루기   
  이벤트: 웹브라우저나 사용자가 행하는 어떤 동작으로 주로 마우스나 키보드를 사용할 때, 웹문서를 불러올 때, 폼에 내용을 입력할 때 주로 발생      
  이벤트 처리기 = 이벤트 핸들러: 이벤트와 이벤트 처리 함수를 연결해 주는 것으로 이벤트 이름 앞에 on을 붙임   
``` javascript  
  예)function showDetail() {    
   document.queryselector('#desc').style.display = "block";   
   ->상세 설명내용을 화면에 표시   
   document.queryselector('#open').style.display = "none";   
   ->상세 설명보기 버튼을 감춤   
     
  function hideDetail() {   
   document.queryselector('#desc').style.display = "none";   
   document.queryselector('#open').style.display = "block";   
     
   <div id="item">   
    <img src = "images/flower.jpg" alt="">   
    <button class="over" id="open" onclick="showDetail()">   
    상세설명보기</button>   
   </div>   
     
  <div id="desc" class="detail">   
    <h4>상세설명</h4>   
    <p>상세설명내용</p>   
   <button id="close" onclick="hideDetail()">   
    상세설명닫기</button>   
  </div>   
   
   ## 여러 이벤트 처리기 연결하기   
   <img src = "images/flower.jpg" alt="" id="cover">   
      
   var coverImage = document.queryselector("#cover");   
   coverImage.onclick = function() {   
    alert('눌렀습니다.');   
    };   
   coverImage.onmouseover = function() {     
    coverImage.style.border = "5px black solid";   
    };   
   coverImage.onmouseout = functon() {   
    coverImage.style.border = "";   
    };   
```

## 객체
    -> 숫자, 문자열 등 여러가지 자료형이 포함되는 복합자료형으로 자료를 저장하고 처리하는 기본단위    
    1. 내장객체   
    -> 자바스크립트 프로그래밍을 할 때 자주 사용하는 요소는 자바스크립트 안에 미리 객체로 정의   
    -> 예를 들어 날짜나 시간과 관련된 프로그램을 작성할 때는 Date객체를 사용해 현재 시각을 알아내고 그 정보를 손쉽게 가져다 사용   
    2. 문서 객체 모델(DOM) - 내장객체   
    -> 객체를 사용해 웹문서를 관리하는 방식   
    -> 예를 들어 웹문서 자체를 담는 Document객체, 웹문서 안의 이미지를 관리하는 Image객체 등   
    3. 브라우저 객체 모델 - 내장객체   
    -> 웹브라우저의 주소표시줄이나 창크기 등 웹브라우저 정보를 객체로 다루는 것   
    -> 예를 들어 사용 중인 브라우저 종류나 버전을 담고 있는 Navigator객체, 브라우저에서 방문한 기록을 남기는 History객체, 주소표시줄 정보를 담고 있는   
    Location객체, 화면크기정보가 들어 있는 Screen객체 등   
    4. 사용자 정의 객체   
    -> 여러 정보를 하나로 묶어 사용해야 할 때 사용자가 직접 객체를 만듦   
        
## 객체의 속성과 매서드   
    1. 속성   
    -> 객체에서 값을 담고 있는 정보   
    -> 객체의 속성 값을 가져올 때는 객체 이름 뒤에 마침표(.)를 찍고 그 뒤에 속성 이름을 적음    
    -> 예)navigator.vendor   
         "Google Inc"   
    2. 매서드   
    -> 객체가 어떻게 동작할지를 선언해 놓은 함수   
    -> 객체 안에 정의된 함수   
    -> 객체 이름 다음에 마침표(.)를 찍고 그 뒤에 매서드를 지정   
    -> 예)window.alert("안녕하세요?")   
    -> window객체는 모든 객체를 품고 있는 최상위 객체이기 때문에   
    window객체의 함수를 실행할 때는 window와 마침표를 빼고 alert("내용")처럼 함수 이름만 사용 가능   
## 객체의 프로토타입과 인스턴스   
    1. 프로토타입(Prototype)   
    -> 웹이미지를 안들기 위한 기본 틀(예시)   
    -> 예를 들어 Image객체는 모든 웹 이미지가 공통으로 가지는 속성과 기능을 모아 놓은 것   
       
    2. 인스턴스   
    -> 프로토타입을 사용해 만들어 낸 객체   
    -> new 예약어 뒤에 프로토타입 객체 이름과 괄호()를 씀   
    -> 예) var now = new Date()   
    now는 이제 Date객체의 인스턴스이고, Date객체에서 정의한 속성과 함수를 모두 사용   
        
## 내장객체로 무작위 수 프로그램 만들기   
    -> Math객체는 삼각함수나 로그함수를 비롯한 수학연산 함수를 가지고 있는 내장객체   
    -> random()함수는 0과1 사이의 무작위 숫자가 표시(0에서 0.99...까지)    
    1부터 100까지 숫자 중에서 무작위 수를 구하고 소수점 이하를 버리려면 Math.floor(Math.random()*100+1)   
    -> Math객체는 따로 인스턴스를 생성하지 않음   
       
## 리터럴 표기법   
    -> 변수를 선언하면서 동시에 값 10을 지정하는 것   
    -> var a = 10;   
    예) var book = {   
          title: "자바스크립트",   
          author: "고쌤",   
          pages: 500,   
          price: 15000,    
          info: function() {   
                  alert(this.title+"책의 분량은"+this.pages+"쪽입니다.");   
                    }    
                 };    
        book.title    
        "자바스크립트"     
        
        book.field = "IT"    
        -> book객체에 분야정보를 추가할 때    
## 생성자 함수    
    -> 객체를 만들어 내는 함수    
    예) function Book(title, author, volume, price) {     
            this.title = title;   
            this.author = author;   
            this.volume = volume;   
            this.price = price;   
          }    
          var html = new Book('웹표준의 정석','ko','608','28000');   
          -> html 객체는 Book객체의 인스턴스    
          var youtube = new Book('유튜브 영상 만들기','kim','368','16000');   
          var python = new Book('점프투 파이썬','park','352','18800');   
          var bookList = [html, youtube, python];   
          -> 배열에 객체를 담을 수 있음   
## 기념일 계산기 
   1. new Date("2021-07-11T18:00:00")   
   -> 대문자 T를 추가한 후 시간을 입력   
   -> 특정 날짜를 저장한 Date객체 생성   
   -> ISO형식(YYYY-MM-DDTHH:MM:SS)   
   2. 날짜/시간 정보를 가져오는 함수   
   -> getMonth()함수와 getDay()함수는 결과값이 0부터 시작   
   ㄱ. getDay()    
   -> 날짜 정보에서 요일(Day)정보를 가져옴   
   -> 0:일요일에서 6:토요일   
   ㄴ. getTime()   
   -> 1970년 1월 1일 이후의 시간을 밀리초로 표시    
   -> 밀리초는 1/1000초     
   3. 오늘 날짜로 부터 50일이 지난 후의 날짜를 계산하는 방법        
   var now = new Date();    
   now.setDate(now.getDate()+50)   
   4. 며칠 만났는지 계산하는 방법    
   var now = new Date();   
   -> 오늘 날짜 정보를 Date객체의 인스턴스 now객체로 만듦   
   var firstDay = new Date("2018-03-23");   
   -> 처음 만난 날의 날짜 정보를 firstDay 객체로 만듦   
   var toNow = now.getTime();   
   -> 오늘 날짜를 밀리초로 바꿈   
   
   

                 
    
    
    
    


