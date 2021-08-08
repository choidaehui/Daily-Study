## 자바스크립트 표기법   
``` javascript
    1. function myFunc() {
          console.log('Hello!');   
          }; (o)  
          
       function myFunc() { console.log('Hello!'); }; (x)   
       
       if(dayOfWeek === 7 && weather === 'sunny') {   
       ...} (o)   
       if(dayOfWeek===7&&weather==='sunny') {  
       ...} (x)
       
    2. let playScore = 0; (o)  
       let speed = distance/time; (o)   
       
       let thisIsaVeryLongVariableThatRecords = 0; (x)   
       let s = d/t;  (x)
       
    3. let myName = 'chris';
       console.log(myName);   
       -> let 대신에 const로 교체   
       
       const myAge = 40;   
       myAge++;
       console.log('Happy birthday!');
       -> const 대신에 let로 교체   
       
    4. let status = (age >= 18) ? 'adult':'minor'; (o)   
    
    5. name === 'chris'; (o)
       age !== 25; (o)
       name == 'chris'; (x)
       age != 25; (x)
       x == true; (o)
       y != false; (o)
       
    6. if(iceCream) {
         alert('Woo hoo!'); 
         } (o) 
         
    7. let myName = 'chris'; 
         console.log('Hi! I'm ${muName}!');   
         
    8. DOM 노드에 문자열을 삽입할 때는 innerHTML 속성이 아니라 textContent 속성 사용   
       예) let text = "Hello";
           const para = document.createElement('P');
           para.textContent = text; (o)
           
    9. let cats = ['Athena', 'Luna']; 
         for(let i of cats) {
              console.log(i);
              } (o)
       let cats = ['Athena', 'Luna'];
         for(i of cats) { 
              console.log(i);
              } (x)
              
    10. 함수 이름은 lowerCamel 표기법 사용, 클래스 이름과 객체 이름은 upperCamel 표기법 사용, 객체 속성과 메소드 이름은 lowerCamel 표기법 사용
        예) function SayHello() {
               alert('Hello!');
               } (x)
            let hanSolo = new Person('Han Solo', 25, 'male');
            let hanSolo = { 
                  name: 'Han Solo',
                  age: 25,
                  gender: 'male'
                  } (o) 
                  
     11. 함수 정의할 때 
        예) let sum = function(a,b) {
                        return a + b;
                        }  (x)
                        
           const array1 = [1,2,3,4];  
           let sum = array1.reduce(function(a, b) {
                       return a + b;
                       });  (o)
        =  const array1 = [1,2,3,4];
           let sum = array1.reduce((a, b) => 
                       a + b 
                       );   (o)
                       
      12. 객체 생성할 때
         예) let myObject = {};  (o)
             let myObject = new Object();  (x)
             
      13. 객체 클래스 생성할 때
         예) class Person {
               constructor(name, age, gender) {
                   this.name = name;
                   this.age = age;
                   this.gender = gender;
                   }
                greeting() {
                   console.log('Hi! I'm ${this.name}');
                   }; 
                 }
                 
       14. 상속관계일 때
          예) class Teacher extends Person {
          .....
          }
       
       15. 배열 생성할 때 
          예) let myArray = [];  (o) 
              let myArray = new Array(length);  (x)
              
       16. 배열 추가할 때
          예) const pets = [];
              pets.push('cat');  (o)
              pets[pets.length] = 'cat';  (x)
              
       17. Error 처리할 때 
          try {
            console.log(results);
            }
          catch(e) {
            console.error(e);
            }
```          
        
       
