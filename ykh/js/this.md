# This

## 실행 컨텍스트 (EC; Execution Context)

> JS 코드를 실행하기 위한 정보를 모아놓은 객체 (환경)

### 순서

1. JS 엔진이 변수, arguments 객체, 함수, Scope 스캐닝 및 this 바인딩

2. 콜 스택에 1의 정보로 만든 실행 context 객체 push

3. 코드 실행

4. 더 실행할 코드가 없으면 현 실행 context를 콜 스택에서 pop

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
   
   2. bind( )

## 참고자료

[[Javascript] Execution Context와 Lexical Environment](https://iamsjy17.github.io/javascript/2019/06/10/js33_execution_context.html)  *by Jewoo.Song*