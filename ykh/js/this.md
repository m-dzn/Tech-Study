# This

## 실행 컨텍스트 (EC; Execution Context)

> JS 코드를 실행하기 위한 정보를 모아놓은 객체 (환경)



### 용어

* Caller :  다른 컨텍스트를 실행하는 컨텍스트

* Callee :  실행되는 컨텍스트



### 종류

**Global 실행 컨텍스트**

* 프로그램과 생명주기를 같이 한다

**Functional 실행 컨텍스트**

* 함수 실행문을 만나면 생성된다

**Eval Function 실행 컨텍스트**

* eval( ) 함수 사용 시 생성된다



### 동작 순서

**Creation Phase**

1. VariableEnvironment component 생성
   
   → 변수, arguments 객체, 함수, Scope 정보 등으로 구성

2. this 바인딩

3. LexicalEnvironment 생성
   
   → VariableEnvironment의 사본

4. 콜 스택에 실행 context 객체를 push



**Execution Phase**

4. 코드 실행 및 결과 저장

5. 더 실행할 코드가 없으면 실행 context를 pop 후 결과 반환



### 컨텍스트 생명주기

1. Global EC 생성

2. 실행 스택에 Push

3. 함수 호출문을 만나면 Functional EC 생성

4. 실행 스택에 Push 후 실행
   
   → 실행이 끝난 컨텍스트는 스택에서 pop

5. Global EC 제거 (pop)
   
   ⇒ 프로그램 종료



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



## 문법적 범위 (LS; Lexical Scope)

> 함수를 선언한 위치에 따라 this가 결정되는 것
> 
> *호출 위치에 따라 결정되는 Dynamic Scope와 다르다*



* JS 함수들은 기본적으로 Lexical Scope를 따른다



```javascript
var name = '홍길동';

function wrapper() {
    var name = '이순신';
    getName();
}
function getName() {
    console.log(name);
}

wrapper(); // '홍길동'; (호출 위치와 무
getName(); // '홍길동';
```



## 문법적 환경 (LE; Lexical Environment)

### Environment Record

>  변수와 함수 선언으로 이루어진 공간

* Declarative environment record :  변수와 함수 선언 저장

* Object environment record :  Global Binding Object 저장

### outer

> 부모 환경에 대한 참조

### this



## 참고자료

[[Javascript] Execution Context와 Lexical Environment](https://iamsjy17.github.io/javascript/2019/06/10/js33_execution_context.html)  *by Jewoo.Song*

[Lexical Environment 와 Closure에 대한 이해](https://velog.io/@paulkim/e)  *by paulkim*