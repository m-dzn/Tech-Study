# This

## 실행 컨텍스트 (EC; Execution Context)

> JS 코드를 실행하기 위한 정보로 구성된 환경







전역 실행 컨텍스트

함수 실행 컨텍스트



### EC 고정 방법

1. call( )
   
   > 사용법 :  함수.call(컨텍스트)
   
   ```javascript
   const student = {
       name: '홍길동',
       getName() {
           return this.name;
       }
   }
   
   const getStudentName = student.getName;
   getName();                 // undefined
   getName.call(student);     // '홍길동'
   ```
   
   * 

2. bind( )





## 참고자료

[[Javascript] Execution Context와 Lexical Environment](https://iamsjy17.github.io/javascript/2019/06/10/js33_execution_context.html)  *by Jewoo.Song*


