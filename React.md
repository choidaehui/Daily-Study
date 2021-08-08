
# DO it! 리액트 프로그래밍 정석 정리  
      -> 리액트는 화면 출력에 특화된 프레임워크 이다.
      -> 리액트는 컴포넌트(component)라는 작고 독립적인 코드 블록을 조합하여 빠르고 효율적으로 화면을 구성
      -> 자바스크립트에는 제이쿼리, 핸들바라는 라이브러리가 있음
      -> 자바스크립트 라이브러리는 화면의 일부분만 수정되어도 화면 전체를 다시 그려야 함
      -> 노드 패키지 매니저(npm)라는 프로그램으로 자바스크립트 라이브러리를 관리
      -> npm을 개선한 것이 yarn
      -> 웹팩은 프로젝트에 사용된 파일을 분석하여 기존 웹 문서 파일로 변환하는 도구
      -> 웹 브라우저가 해석할 수 없는 .hbs, .cjs, sass 등의 파일을 웹팩이 분석하여 .js, .css 등의 파일로 변환
      -> 노드제이에스는 구글에서 공개한 소프트웨어로 V8엔진을 기반으로 만든 자바스크립트 런타임 도구이다
      -> NVM은 노드제이에스를 설치하거나 관리해주는 프로그램
      
## 리액트 ES6문법 
      1. 템플릿 문자열
        -> 문자열 안에 변수와 연산식을 혼합하여 사용
        -> 작은 따옴표(')대신 백틱(`)으로 문자열을 표현
        -> 특수기호 $를 사용하여 변수 또는 식을 포함
        
``` javascript 
      var string1 = '안녕하세요';
      var string2 = '반갑습니다';
      var greeting = `${string1} ${string2}`;
      var product = { name: '도서', price: '4200원' };
      var message = `제품 ${product.name}의 가격은 ${product.price}입니다.`;
      // $기호를 사용하여 변수를 포함
      var multiLine = `문자열1
      문자열2`;
      // 템플릿 문자열은 엔터를 눌러 줄 바꿈을 허용
      // 이스케이프 시퀀스(\n)를 사용하지 않아도 됨
      var value = 1;
      var value = 2;
      var boolValue = false;
      var operator1 = `곱셈값은 ${value1 * value2}입니다.`;
      var operator2 = `${boolValue ? '참' : '거짓'}입니다.`;
      // $기호를 사용하여 연산을 포함
      
      var cart = { name: '도서', price: '1500원'};
      var getTotal = function(cart) {
        return `${cart.price}원`;
        };
      var myCart = `장바구니에 ${cart.name}가 있습니다. 총 금액은 ${getTotal(cart)}입니다.`;  
```

    2. 전개 연산자
      -> 나열형 자료를 추출하거나 연결할 때 사용
      -> 배열이나, 객체, 함수 인자 표현식([],{},())안에서만 사용 
      -> 배열이나 객체, 변수명 앞에 마침표 세 개(...)를 입력
      
      ``` javascript 
       var array1 = ['one', 'two'];
       var array2 = ['three', 'four'];
       const combined = [...array1, ...array2];
       // 두 배열 항목을 전개 연산자로 합함
       // 결과: combined = ['one', 'two', 'three', 'four'];
       const [first, second, three = 'empty', ...others] = array1;
       // 결과: first = 'one', second = 'two', three = 'empty', others = []
       // 올바르지 못한 예
       // var wrongArr = ...array1;
       // 전개 연산자를 배열 표현식 없이 사용한 잘못된 예
       
       function func(...args) { var[first, ...others] = args; }
       // 함수 인자 배열을 args변수에 할당
       
       var objectOne = { one: 1, two: 2, other: 0 };
       var objectTwo = { three: 3, four: 4, other: -1 };
       var combined = {
         one: objectOne.one,
         two: objectOne.two,
         three: objectTwo.three,
         four: objectTwo.four,
         };
         //키에 해당하는 값을 추출
         
       var combined = Object.assign({}, objectOne, objectTwo);
       // 결과: combined = { one: 1, two: 2, three: 3, four: 4, other: -1 }
       // 객체 내장 함수 assign()을 사용하여 두 객체를 병합
       // assign()의 첫 번째 인자는 결과로 반환할 객체({}), 나머지 인자는 병합할 객체임
       // 병합할 객체는 앞에 있는 객체부터 덮어 씀
       
       var combined = Object.assign({}, objectTwo, objectOne);
       // 결과: combined = { one: 1, two: 2, three: 3, four: 4, other: 0 }
       // 중복되는 키값이 있으면 이후에 전달된 객체(objectOne)의 값으로 덮어 씀
       
       var others = Object.assign({}, combined);
       delete others.other;
       // 결과: others = { one: 1, two: 2, three: 3, four: 4 }
       
    =  var objectOne = { one: 1, two: 2, other: 0 };
       var objectTwo = { three: 3, four: 4, other: -1 };
       var combined = {
         ...objectOne,
         ...objectTwo,
         };
       // 결과: combined = { one: 1, two: 2, three: 3, four: 4, other: -1 }
       
       var combined = { 
         ...objectTwo,
         ...objectOne,
         };
       // 결과: combined = { one: 1, two: 2, three: 3, four: 4, other: 0 } 
       
       var { other, ...others } = combined;
       // 결과: others = { one: 1, two:2, three: 3, four: 4 }
       // 객체에서 특정 값을 추출할 때는 추출하려는 키 이름(other)을 맞추고, 나머지는 전개 연산자로 선언된 변수(others)에 할당 함       
      ```
    3. 가변 변수와 불변 변수
      -> let은 값을 수정할 수 있는 가변 변수
      -> const은 값을 수정할 수 없는 불변 변수
      -> 불변 변수는 값을 다시 할당할 수 없는 것이지 값을 변경할 수 있음
      
      ``` javascript 
        const arr2 = [];
        arr2.push(1);
        // 결과: arr2 = [1]
        arr2.splice(0, 0, 0);
        // 결과: arr2 = [0. 1]
        arr2.pop();
        // 결과: arr2 = [1]
        const obj2 = {};
        obj2['name'] = '내이름'; 
        // 결과: obj2 = { name: '내이름' }
        Object.assign(obj2, { name: '새이름' });
        // 결과: obj2 = { name: '새이름' }
        delete obj2.name;
        // obj2 = {}
        // 불변 변수에 새값을 할당하는 방법으로 새로 정의하여 무결성 
        
        const num1 = 1;
        const num2 = num1 * 3;
        // num2 = 3
        const str1 = '문자';
        const str2 = str1 + '추가';
        // str2 = '문자추가'
        const arr3 = [];
        const arr4 = arr3.concat(1);
        // arr4 = [1]
        const arr5 = [...arr4, 2, 3];
        // arr5 = [1, 2, 3]
        const arr6 = arr5.slice(0, 1);
        // arr6 =[1], arr5 = [1, 2, 3]
        const [first, ...arr7] = arr5;
        // arr7 = [2, 3], first = 1
        const obj3 = { name: '내이름', age: 20 };
        const objValue = { name: '새이름', age: obj3.age };
        const obj4 = {...obj3, name: '새이름' };
        // obj4 = { name: '새이름', age: 20 }
        const { name, ...obj5 } = obj4;
        // obj5 = { age: 20 }
      ```
    4. 클래스
    
      
      
      
      
