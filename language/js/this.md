# This

## this (실행 컨텍스트) 고정 방법

1. call( )
   
   > 사용법 :  함수.call(컨텍스트, 인수1, 인수2, ...)
   
   ```javascript
   const student = {
       name: '홍길동',
       getName(age) {
           console.log(this.name, age);
       }
   }
   
   const getStudentName = student.getName;
   getStudentName();                     // undefined
   getStudentName.call(student, 30);     // 홍길동 30
   ```
   
   <br>

2. apply( )
   
   > 사용법 : 함수.apply(컨텍스트, [인수1, 인수2, ...])
   
   ```javascript
   const student = {
       name: '홍길동',
       getName(age) {
           console.log(this.name, age);
       }
   }
   
   const getStudentName = student.getName;
   getStudentName();                        // undefined
   getStudentName.apply(student, [30]);     // 홍길동 30
   ```
   
   <br>

3. bind( )
   
   > 사용법 : 함수.bind(컨텍스트) 후 일반 함수처럼 실행
   
   ```javascript
   const student = {
       name: '홍길동',
       getName(age) {
           console.log(this.name, age);
       }
   }
   
   const getStudentName = student.getName.bind(student);
   getStudentName(30);    // 홍길동 30
   ```