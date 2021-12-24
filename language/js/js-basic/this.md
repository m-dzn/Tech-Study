# This

## function( ) 과 화살표 함수의 this 차이

### function( )

자기 자신만의 Lexical Scope를 갖기 때문에 this는 function의 스코프를 가리킵니다.

### 화살표 함수

별도의 스코프를 갖지 않고 부모 환경의 Lexical Scope를 참조합니다.

## this (실행 컨텍스트) 고정 방법

1. call( )
   
   > 사용법 : 함수.call(컨텍스트, 인수1, 인수2, ...)
   
   ```javascript
   const student = {
       name: '홍길동',
       getName(age) {
           console.log(this.name, age);
       }
   }
   
   const getStudentName = student.getName;
   getStudentName();                     // undefined
   getStudentName.call(student, 30);     // 홍길동 30
   ```
   
   \

2. apply( )
   
   > 사용법 : 함수.apply(컨텍스트, \[인수1, 인수2, ...])
   
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

## Node의 this

> Node에서 전역 스코프의 this는 module.exports
> 함수 스코프에서 this는 global 객체를 나타냅니다.