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
         var toFirst = firstDAy.getTime();   
         -> 처음 만난 날을 밀리초로 바꿈   
         var passedTime = toNow - toFirst;   
         -> 처음 만난 날과 오늘 사이의 차이(밀리 초 값)   
         var passedDay = Math.round(passedTime/(1000*60*60*24));    
         -> 밀리초를 날짜수로 변환한 후 반올림   
         document.queryselector("#accent").innerText = passedDay+"일"   
         -> #accent 영역에 표시   
             
         5. 100일 후 날짜 계산하는 방법   
         var future = toFirst + 100 * (1000*60*60*24);   
         -> 처음 만난 날에 100일을 더함   
         var someday = new Date(future);   
         -> future값을 사용해 Date객체의 인스턴스를 만듦    
         var year = someday.getFullyear();   
         var month = someday.getMonth()+1;   
         var date = someday.getDate();   
         document.queryselector('#date100").innerText = year+"년"+month+"월"+date+"일";   
            
         6. calcDate()함수로 기념일 계산하는 방법   
         function calcDate(days) {   
            var future = toFirst + days * (1000*60*60*24);    
            var someday = new Date(future);   
            var year = someday.getFullyear();   
            var month = someday.getMonth()+1;   
            var date = someday.getDate();   
            document.queryselector('#date"+days).innertext = year+"년"+month+"월"+date+"일";    
            } 
## 배열
        -> 여러 개의 항목을 하나의 변수에 저장   
        예) var myArray = new Array();   
        -> Array객체의 인스턴스를 만들기   
        var numbers = ["one","two","three","four"];   
        -> 리터럴을 사용한 배열   
        var numbers = new Array("one","two","three","four");   
        -> Array객체를 사용한 배열   
             
        1. 둘 이상의 배열을 연결하는 concat()함수   
        -> 기존의 배열에 또 다른 배열이나 값을 합쳐서 새로운 배열을 만드는 함수   
        예) var nums = ["!","2","3"];   
        var chars = ["a","b","c","d"];   
        nums.concat(chars)   
        -> nums배열에 chars배열 연결   
        -> ["1","2","3","a","b","c","d"]   
           
        2. 배열요소를 연결하는 join()함수   
        -> 배열요소를 연결하는 함수로 함수에서 구분기호를 정하지 않으면 쉼표(,)로 요소를 구분   
        예) nums.join()   
        -> 구분기호 없이 연결   
        "1,2,3"   
        nums.join("-")   
        -> 구분기호("-")를 사용해 연결   
        "1-2-3"  
        myColor = ["red","green","blue"];   
        myColor.join("+")   
        colorString = "red + green + blue";   
           
        3. push()함수   
        -> 배열의 맨 끝에 요소를 추가   
        var nums = ["1","2","3"]   
        nums.push("4","5")   
        -> nums배열 맨 끝에 "4"와"5"요소 추가   
        nums   
        ["1","2","3","4","5"]   
           
        4. unshift()함수   
        -> 배열의 맨 앞에 추가   
        예) nums.unshift("0")   
        -> nums배열 맨 앞에 "0" 요소 추가   
        nums   
        -> ["0","1","2","3","4","5"]   
            
        5. pop()함수   
        -> Array객체에서 맨 뒤에 있는 요소를 추출할 때   
        -> 배열에서 요소를 추출하면 해당 요소가 배열에서 빠지면서 배열이 수정    
        예) var study = ["html","css","javascript"]   
        study.pop()   
        "javascript"   
        study   
        ["html","css"]   
           
        6. shift()함수   
        -> 배열의 첫 요소 반환   
        -> 해당 요소가 배열에서 빠지면서 배열이 수정   
        예) var js = ["es6+","node","react","angular","vue"]  
        js.shift()   
        "es6+"   
           
        7. splice()함수   
        -> 괄호 안에 들어 있는 인수에 따라 일정구간의 요소를 삭제하고 새로운 요소를 추가   
        -> 삭제한 구간의 요소들로 이루어진 새로운 배열이 결과값으로 표시   
        예) var numbers = [0,1,2,3,4,5]   
        numbers.splice(2)   
        -> 인덱스2(세번째 요소)이후 끝까지 삭제   
        [2,3,4,5]   
        -> 삭제된 요소로 이루어진 배열   
        numbers   
        [0,1]   
        -> 수정된 원래 배열   
           
        ㄱ. splice() 함수에 인수가 2개일 경우   
        -> 첫 번째 인수는 인덱스 값이고, 두 번째 인수는 삭제할 개수   
        예) var study = ["html","css","web","jquery"]   
        study.splice(2,1)   
        -> 인덱스 2에서 한 개 삭제   
        ["web"]   
        -> 삭제된 요소로 이루어진 배열   
        study   
        ["html","css","jquery"]   
        -> 수정된 원래 배열   
           
        ㄴ. splice()함수에 인수가 3개일 경우   
        -> 세 번째 인수는 앞서 삭제한 위치에 새로 추가할 요소를 지정   
        예) study.splice(2,1,"js")   
        ["jquery"]   
        -> 인덱스 2에서 1개 삭제   
        study   
        ["html","css","js"]   
        -> 삭제한 자리에서 새로운 요소를 추가   
        var chars = ["a","e","f"]   
        chars.splice(1,0,"b","c","d")
        []   
        chars   
        ["a","b","c","d","e","f"]   
        ->새로운 요소 3개 추가   
           
        8. slice()함수   
        -> 원하는 위치의 요소들을 추출   
        예) var colors = ["red","green","blue","white","black"]   
        colors.slice(2)   
        ["blue","white","black"]   
        -> 인덱스 2부터 끝까지 추출   
        colors   
        ["red","green","blue","white","black"]   
        -> 원래 배열은 변경되지 않음   
        var colors2 = colors.slice(1,4)   
        colors2   
        ["green","blue","white"]   
        -> 두 번째 요소(인덱스1)부터 네번째 요소(인덱스3)까지 추출해서 새로운 배열 colors2생성   
        colors   
        ["red","green","blue","white","black"]   
        ->원래 배열은 변경되지 않음   
           
# 여행준비물 점검 프로그램 만들기   
        var itemList = new Array();   
        =var itemList = [];   
        var addBtn = document.querySelector("#add");   
        -> #add인 요소를 가져와 addBtn으로 저장    
        addBtn.addEventListener("click",addList);   
        -> addBtn을 클릭하면 addList함수 실행   
        function addList() {   
            var item = document.querySelector("#item").value;   
            -> 텍스트 필드 내용을 가져옴   
            if(item != null) {   
                   itemList.push(item);   
                   -> itemList배열 끝에 item 변수 값 추가   
                   document.querySelector("#item").value = "";   
                   -> id = "item"인 요소 값을 지움   
                   document.querySelector("#item").focus();   
                   -> 텍스트 필드에 focus()함수 적용   
                   }   
        function showList() {   
            var list = "<ul>";   
            -> 목록을 시작하는 <ul>태그 저장   
            for(var i=0; i<itemList.length; i++) {   
               list += "<li>" + itemList[i] + "</li>";   
               -> 각 요소를 <li> ~ </li>로 묶음   
               }   
               list += "</ul>";   
               document.querySelector("#itemList).innerHTML = list;   
               -> list 변수값 표시   
               }   
# 챙긴 준비물 목록에서 지우기   
        function showList() {      
             ... ...
             for(var i=0; i<itemList.length; i++) {    
                list += "<li>" + itemList[i] + "<span class='close' id="+i+"> X </span></li>";   
                var remove = document.querySelectorAll(".close");   
                -> 삭제 버튼을 변수로 저장. 배열형태가 됨   
                }   
                
             for(var i=0; i<remove.length; i++) {   
                  remove[i].addEventListener("click",removeList);   
                  }   
                -> 요소를 클릭하면 removeList()실행   
        function removeList() {   
             console.log(this);   
               -> this 값을 콘솔 창에 표시   
             var id = this.getAttribute("id");   
             itemList.splice(id,1);   
               -> itemList 배열에서 인덱스 값이 id인 요소 1개 삭제   
             showList();   
               -> 변경된 itemList 배열을 다시 화면에 표시   
             }   
# 문서객체모델(DOM)   
        -> 웹 문서의 모든 요소를 자바스크립트를 이용하여 조작할 수 있도록 객체를 사용해 문서를 해석하는 방법   
        1. DOM을 사용해 상세설명 가리기   
           document.querySelector('#detail h3').style.visibility = 'hidden'   
           document.querySelector('#detail p').style.visibility = 'hidden'   
        2. DOM 트리   
           ㄱ. 웹 문서의 태그는 요소(element)노드로 표현   
           ㄴ. 태그가 품고 있는 텍스트는 해당 요소 노드(태그)의 자식 노드인 텍스트(Text)노드로 표현   
           ㄷ. 태그의 속성은 모두 해당 요소 노드(태그)의 자식 노드인 속성(Attribute)노드로 표현   
           ㄹ. 주석은 주석(Comment)노드로 표현   
             -> 웹 문서를 놓고 DOM 트리를 상상하면 자바스크립트로 원하는 요소에 어떻게 접근할 지 쉽게 생각 가능   
        3. DOM 요소에 접근하기   
          -> DOM 요소에 접근할 때는 주로 선택자를 사용   
          ㄱ. DOM 요소를 id선택자로 접근하는 함수(getElementById())   
            예) document.getElementById("heading").onclick = function() {   
                    this.style.fontsize = "5em"   
                  }   
                -> id가 heading인 제목을 누르면 접근한 요소의 글자 크기가 커짐   
            예) document.getElementById("desc")   
                -> <div id = "desc"> 태그의 텍스트 부분에 접근    
          ㄴ. DOM 요소를 class 값으로 찾아내는 함수(getElementsByClassName())   
               -> class 선택자는 id 선택자와 다르게 웹 문서 안에서 여러 번 사용 가능    
               -> 2개 이상의 웹 요소에 접근   
               예) document.getElementsByClassName("accent")   
               -> class 값이 accent인 요소가 배열 형태로 저장됨   
               -> class 값이 accent인 웹 요소들에 접근   
               예) document.getElementsByClassName("accent")[0]   
               -> 배열의 인덱스를 사용하여 첫 번째 요소에 접근   
               예) document.getElementsByClassName("accent")[0].style.textDecoration = "underline"   
               <span class = "accent">게뎁농장</span>   
               -> '게뎁농장'텍스트에 밑줄이 생성 됨  
          ㄷ. DOM 요소를 태그 이름으로 찾아내는 함수(getElementsByTagName())   
               -> id나 class 선택자가 없는 DOM 요소에  태그 이름을 찾아 DOM 요소에 접근   
               -> 여러 DOM 요소들에 접근   
               예) document.getElementsByTagName("h2")[0].style.backgroundColor = "#eee"   
               -> h2 태그 이름으로 접근한 DOM요소 중 첫 번째 요소의 배경색을 바꿈   
          ㄹ. DOM 요소를 id, class, 태그 이름으로 찾아내는 함수(querySelector(), querySelectorAll())   
               -> id 값 'container'인 DOM 요소에 접근하는 방법 비교   
               = document.getElementById("container")   
               = document.querySelector("#container")   
               예) class 값이 'accent'인 DOM 요소들에 접근   
               = document.querySelectorAll(".accent")   
               예) document.querySelectorAll(".accent")[1].style.backgroundColor = "yellow"   
               -> class 값이 'accent'인 두 번째 요소에 접근한 다음 요소의 배경색을 노란색으로 바꿈   
               -> 웹 요소 정도만 변경한다면 getElementById(), getElementsByClassName(), getElementsByTagName()함수를 사용하고,   
               웹 요소 뿐만 아니라 요소의 텍스트나 속성을 변경하거나 새로운 노드를 추가하고 싶다면 querySelector(), querySelectorAll() 함수를 사용    
          ㅁ.  HTML 태그 속성을 가져오거나 수정하는 함수(getAttribute(), setAttribute())   
               -> 선택한 상품 이미지를 특정 위치에 표시   
                 a. 이미지 요소에 접근하는 것   
                    -> querySelector()함수 사용   
                 b. 속성에 접근   
                    -> getAttribute()함수 사용   
                 c. 접근한 속성 값 변경   
                    -> setAttribute()함수 사용   
                 예) <div id="prod-img">   
                       <img src="images/coffee-pink.jpg" alt="에디오피아 게뎁">   
                     </div>   
                 예) document.querySelector("#prod-img>img").setAttribte("src","images/coffee-blue.jpg")   
                    -> 화면에 표시되는 그림이 변경 됨   
           ㅂ. 사용자가 누른 작은 이미지를 큰 이미지 위치에 표시   
              <div id="prod-pic">   
               <img src="images/coffee-pink.jpg" alt="에디오피아 게뎁" id="cup" width="200" height="200>   
                <div id="small-pic">   
                 <img src="images/coffee-pink.jpg" class="small">
                 <img src="images/coffee-blue.jpg" class="small">
                 <img src="images/coffee-gray.jpg" class="small">
                </div>
              </div>
                예) var bigPic = document.querySelector("#cup");   
                    -> 큰 이미지 가져옴   
                    var smallPics = document.querySelectorAll(".small");
                    -> 작은 이미지 가져옴   
                    for(var i=0; i<smallPics.length; i++) {
                    -> 노드(웹 문서에 있는 요소나 속성)리스트의 각 요소에 접근   
                    smallPics[i].onclick = showBig;   
                    -> 요소를 누르면 showBig()함수 실행   
                    }   
                    function showBig() {
                      var newPic = this.src;   
                      -> click 이벤트가 발생한 대상의 src 속성 값 가져옴   
                      bigPic.setAttribute("src",newPic);   
                      -> newPic의 값을 bigPic 속성값에 할당 함   
                      }   
                  = for(var i=0; i<smallPics.length; i++) {
                     smallPics[i].onclick = function(event) {
                       bigPic.src = this.src;
                       }
                    }
        4. DOM에서 이벤트 처리하기   
              ㄱ. HTML 태그 안에서 이벤트 처리기 연결하기    
                예) <div id="container">   
                      <img id="pic" src="images/girl.png" alt="" onclick="changePic()">   
                      -> 누르면 changePic()함수 실행   
                    </div>   
                    <script>   
                      var pic = document.querySelector('#pic');   
                      function changePic() {
                        pic.src = "images/boy.png";   
                        }   
                    </script>   
               ㄴ. DOM요소에 이벤트 처리기 연결하기   
                 예) <div id="container">   
                      <img id="pic" src="images/girl.png" alt="">   
                     </div>   
                     <script>   
                       var pic = document.querySelector('#pic');   
                       pic.onclick = changePic;   
                       ->pic 요소를 누르면 changePic()함수 실행   
                       function changePic() {
                         pic.src = "images/boy.png";   
                         }   
                     </script>   
                ㄷ. addEventListener()함수 사용하기    
                   -> 한 요소에 여러 이벤트가 발생했을 때 이를 동시에 처리   
                   예) var pic = document.querySelector('#pic');   
                       pic.addEventListener("mouseover",changePic,false);   
                       -> true이면 캡처링, false이면 버블링, 기본값 false   
                       -> 캡처링은 DOM의 부모노드에서 자식노드로 이벤트가 전달   
                          버블링은 DOM의 자식노드에서 부모노드로 이벤트가 전달   
                       pic.addEventListener("mouseout",originPic,false);   
                       function changePic() {
                         pic.src = "image/boy.png";   
                         }   
                       function originPic() {
                         pic.src = "images/girl.png";
                         }   
                       예) document.addEventListener('click',function() {alert("Hello");});   
                       -> 웹 문서의 어디를 누르든지 '안녕하세요?'라는 알림창이 나타남   
        5. DOM으로 CSS 속성에 접근하고 수정하기   
                   var myRect = document.querySelector('#rect');   
                   myRect.addEventListener("mouseover",function() {
                     myRect.style.backgroundColor = "green";   
                     myRect.style.borderRadius = "50%";   
                     });   
                     -> mouseover이벤트 시 myRect요소의 배경색과 테두리 변경   
                   myRect.addEventListener("mouseout",function() {   
                     myRect.style.backgroundColor = "";   
                     myRect.style.borderRadius = "";   
                     });   
                     -> mouseout 이벤트 시 myRect 요소의 배경색을 지우고 테두리 둥글게 처리한 것 취소   
                ㄱ. 웹 요소를 화면에 표시하기/감추기   
                   -> CSS속성 중 display: none;을 사용해서 웹 요소를 화면에서 감추면 그 요소가 차지하던 공간도 사라지고,   
                      visibility: hidden;을 사용해서 웹 요소를 감추면 요소가 있던 공간은 빈 상태로 남아있게 됨   
                   -> display: block;을 사용하면 화면에 웹 요소를 표시   
                ㄴ. 상세 설명보기/닫기   
                   var isOpen = false;   
                   var view = document.querySelector('#view');   
                   view.addEventListener("click",function() {   
                     if(isOpen == false) {   
                       document.querySelector('#detail').style.display = "block";   
                       -> 상세 정보를 화면에 표시   
                       view.innerText = "상세설명닫기";   
                       isOpen = true;   
                       -> 화면 표시 상태로 지정   
                       }
                       else {   
                          document.querySelector('#detail').style.display = "none";   
                          -> 상세 정보를 화면에서 감춤   
                          view.innerText = "상세설명보기";   
                          isOpen = false;   
                          -> 화면에서 감춰진 상태로 지정   
        6. DOM에 요소 추가하기   
             -> 웹 문서 상에 없던 요소를 추가해서 화면에 표시   
             -> DOM트리에 새로운 노드를 추가   
             ㄱ. 요소 노드 만들기(createElement()함수)   
                예) var newP = document.createElement("p")   
                    -> <p>태그에 해당하는 요소 노드를 만듦   
             ㄴ. 텍스트 노드 만들기(createTextNode()함수)   
                예) var newText = document.createTextNode("주문이 완료되었습니다.")   
             ㄷ. 자식 노드를 추가하기(appendChild()함수)   
                -> 텍스트 노드를 요소 노드의 자식 노드로 연결   
                -> 요소 노드를 다른 요소 노드의 자식 노드로 연결   
                -> 자식 노드가 여럿일 경우 자식 노드 중 맨 끝에 추가   
                예) newP.appendChild(newText)   
                예) document.body.appendChild(newP)   
                -> <p>태그 소스를 웹 문서의 <body>태그 안에 추가(자식 노드로 추가)   
             ㄹ. 속성 노드 만들기(createAttrubute()함수)   
                -> 함수의 괄호 안에 추가할 속성 이름을 지정   
                예) var attr = document.createAttribute("class")   
                        attr.value = "accent"   
             ㅁ. 속성 노드 연결하기(setAttributeNode()함수)   
                -> 앞에서 선언한 <p>태그 요소 노드에 속성 노드 연결   
                -> 속성 노드를 요소 노드에 연결할 때 사용   
                예) newP.setAttributeNode(attr)   
                    null   
                    -> 속성 노드를 요소노드에 연결하고 반환값이 null임   
                  = newP.setAttribute("class","accent")   
                  예) var easys = document.createAttribute("id")   
                       easys.value = "doit_js"   
                       -> easys라는 속성 노드를 만들고 id="doit_js" 속성 값을 지정   
             ㅂ. 참가 신청 명단 프로그램 만들기   
                예) <form action="">   
                      <input type="text" id="userName" placeholder="이름" required>   
                      <button onclick = "newRegister(); return false;">신청</button>   
                    </form>   
                    -> return false를 추가하는 것은 원래 버튼의 기능(입력 내용을 서버로 전송하는 기능)을 사용하지 않은 것   
                    function newRegister() {   
                       var newP = document.createElement("P");   
                       var userName = document.querySelector("#userName");   
                       var newText = document.createTextNode(userName.value);   
                       newP.appendChild(newText);   
                       -> newText노드를 newP노드의 자식 노드로 연결
                       var nameList = document.querySelector('#nameList");    
                       nameList.appendChild(newP);
                       -> newP노드를 nameList노드의 자식 노드로 연결   
                       userName.value = "";   
                       -> 다음 이름을 입력할 수 있도록 텍스트 필드 비우기   
        7. 추가한 노드 순서 바꾸거나 삭제하기   
               ㄱ. 배열 형식에 여러 값을 저장하듯 여러 노드가 하나의 변수에 저장된 것
               -> 노드 리스트   
               예) document.querySelectorAll("p")[0]   
               -> P노드를 저장한 노드 리스트 중에서 첫 번째 노드를 가져 옴   
               ㄴ. hasChildNodes()함수   
               -> 특정 노드에 자식 노드가 있는지를 확인하는 함수   
               -> 자식 노드가 있다면 true, 없다면 false를 반환   
               예) document.querySelectorAll("P")[0].hasChildNodes()   
                   true    
                   -> 첫 번째 P노드에는 자식노드가 있음   
         8. 자식 노드에 접근하기    
         -> 자식 노드가 있다면 childNodes 속성을 사용해서 현재 노드의 자식 노드에 접근   
         -> 요소 노드 뿐만 아니라 태그와 태그 사이의 줄 바꿈도 빈 텍스트 노드인 자식 노드로 인식   
         예) <div id="nameList">   
                 <p>홍길동<span class="del">X</span></p>   
                 <p>백두산<span class="del">X</span></p>   
                 <p>도레미<span class="del">X</span></p>   
             </div>   
             document.querySelector("nameList").childNodes   
             NodeList(7)[text,P,text,P,text,P,text]   
             -> 총 7개 노드   
             -> <div>태그 다음의 줄 빠꿈, <P>태그 사이의 줄바꿈, </div>태그 앞의 줄 바꿈을 빈 텍스트 노드로 인식   
             ㄱ. 요소에만 접근하려면 children속성을 사용   
             예) document.querySelector("#nameList").children   
                 HTMLCollection(3)[P,P,P]   
             ㄴ. 원하는 위치에 노드 삽입하기(insertBefore()함수)
             -> 2개의 인수를 사용   
             -> 첫 번째 인수는 추가하는 노드이고 두 번째 인수는 기준이 되는 노드   
             예) nameList.insertBefore(nameList.children[2], nameList.children[0])
             -> 세 번째 자식 노드를 첫 번째 자식 노드 앞에 추가    
             ㄷ. 특정 노드 삭제하기(removeChild()함수, parentNode 속성)   
               a. removeChild()함수   
               -> 부모 노드에서 자식 노드를 삭제하는 함수이고, 괄호 안에는 삭제하려는 자식 노드가 들어감   
               b. parentNode 속성   
               -> 현재 노드의 부모 요소 노드를 반환   
             ㄹ. 맨 위에 이름 추가하기   
               -> 새로 추가하는 자식 노드를 기존 자식 노드 보다 앞에 추가   
                 (appendChild()함수는 맨 뒤에 추가 됨)   
                 예) var nameList = document.querySelector("#nameList");   
                      nameList.insertBefore(newP,nameList.childNodes[0]);   
                      ->newP변수에 담긴 <P>요소를 #nameList 맨 앞에 추가   
         9. 참가자 명단 프로그램 만들기   
            예) 참가자 명단 생성   
              var newText = document.createTextNode(userName.value);   
              -> 새 텍스트 노드 만들기   
              newP.appendChild(newText);   
              -> 텍스트 노드를 <P>요소의 자식 요소로 연결   
              var delBttn = document.createElement("span");   
              var delText = document.createTextNode("X");   
              delBttn.setAttribute("class","del");   
              -> class 속성 값으로 del을(class="del")생성   
              delBttn.appendChild(delText);   
            예) 참가자 명단 삭제   
              var removeBttns = document.querySelectorAll(".del");   
                 for(var i=0; i<removeBttns.length; i++) { 
                   removeBttns[i].addEventListener("click",function() { 
                     if(this.parentNode.parentNode)   
                       this.parentNode.parentNode.removeChild(this.parentNode);   
                       });   
                       -> 현재 노드(this)의 부모 노드의 부모 노드를 찾아 현재 노드의 부모 노드 <P>노드를 삭제   
                       -> <span>노드가 현재 노드(this)이다.
             
                                                
              
                 
                 
               
                
                
        
             
               
               
               
               
               
               
               
               
               
               
               
               
               
               
               
               
               
               
               
               
               
               
               
               
               
               
               
               
               
                
                   
                   
           
       
        
            
