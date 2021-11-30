# 컨텍스트

## 실행 컨텍스트 (EC)

> **Execution Context**
> 
> JS 코드를 실행하기 위한 정보 (변수, 함수, this, arguments, scope, ...) 를 모아놓은 객체 (환경)

### 기본

#### 특징

- 변수나 함수를 선언 이전에 사용할 수 있게 해줍니다
- 상위 scope의 Lexical Environment에 대한 단방향 Linked List 형태로 외부 환경을 참조합니다

#### 용어

- Caller : 다른 컨텍스트를 실행하는 컨텍스트

- Callee : 실행되는 컨텍스트

#### 종류

**Global 실행 컨텍스트**

- 프로그램 실행 시 생성됩니다
- 프로그램과 생명주기를 같이 합니다

**Functional 실행 컨텍스트**

- 함수 실행문을 만나면 생성됩니다

**Eval Function 실행 컨텍스트**

- eval( ) 함수 사용 시 생성됩니다
- 보안상의 취약점을 갖고 있습니다

#### 동작 순서

**Creation Phase**

1. VariableEnvironment 컴포넌트 생성
   
   → 변수, arguments 객체, 함수, Scope 정보 등으로 구성

2. this 바인딩

3. LexicalEnvironment 컴포넌트 생성
   
   → 현 단계에서는 VariableEnvironment의 사본

4. 콜 스택에 실행 context 객체를 push

**Execution Phase**

> JS 엔진이 한 줄씩 코드를 실행하고 변수에 값을 할당하는 Phase입니다

4. 코드 실행 및 결과 저장

5. 더 실행할 코드가 없으면 실행 context를 pop 후 결과 반환

### 구조

#### EC의 구조

```javascript
ExecutionContext = {
    LexicalEnvironment: [Lexical Environment],
    VariableEnvironment: [Lexical Environment],
    ThisBinding: [object]
}
```

##### Environment Record

> 현재 실행 환경의 식별자 (변수와 함수) 를 담고 있는 공간

- Declarative environment record : 변수와 함수, this, super 등 선언된 식별자 저장

- Object environment record : Global Binding Object 저장

```javascript
Environment Record: {
    Declarative Environment Record,
    Object Environment Record,
    Global Environment Record
}
```

##### outer environment reference

> 부모 Lexical Environment 에 대한 참조

- 스코프 체인을 타고 상위 스코프를 탐색할 때 활용됩니다

##### ThisBinding

**Global 실행 컨텍스트** : global object

**함수 실행 컨텍스트** : 호출 위치에 따라 결정

→ 객체 참조를 통해 호출될 경우? this는 해당 객체

→ 그 외의 경우?

nonstrict mode : global object

strict mode : undefined

#### Environment의 구조

##### 어휘적 환경 (LE)

> **Lexical Environment란?**
> 
> 현재 실행 환경의 변수 및 참조 정보를 담고 있는 객체를 말합니다
> 
> 구체적으로는 **identifier-variable** 쌍을 매핑해 저장한 자료구조라 할 수 있습니다
> 
> let, const 변수가 매핑됩니다

> JS 엔진이 EC를 만들 때 참고할 스펙 정보가 LE입니다

**특징**

1. let, const 변수의 값은 메모리에 매핑될 때 uninitialized로 초기화됩니다
   
   → 값을 초기화하기 전에는 사용할 수 없습니다
   
   → 초기화하지 않고 사용하면 reference error가 발생합니다

2. 매개변수와 함수의 지역변수가 저장됩니다

3. 단위 :  local lexical scope (블록 단위 scope)

**용어**

- identifier : 변수/함수의 이름 (식별자)

- variable : 실제 객체에 대한 참조

**구조**

```javascript
Lexical Environment = {
    environment record: {
        identifier1: [value 또는 function object],
        identifier2: [value 또는 function object],
        ...
    },
    outer environment reference: {}
}
```

##### 변수 환경 (VE)

> **Variable Environment**
> 
> var 변수가 매핑됩니다

**특징**

1. var 변수의 값 (variable) 은 메모리에 매핑될 때 undefined로 자동 초기화됩니다

2. Lexical Environment를 상속합니다

3. 단위 :  functional scope

```javascript
Variable Environment = {
    environment record: {},
    outer environment reference: {}
    ThisBinding: [object]
}
```

### VE와 LE 비교

**VE**

Environment Record : 호이스팅되는 var, 함수 선언문 저장

**LE**

Envoironment Record : 호이스팅되지 않는 let, const 등 저장

### EC 생명주기

1. Global EC 생성

2. 실행 스택에 Push

3. 함수 호출문을 만나면 Functional EC 생성

4. 실행 스택에 Push 후 실행
   
   → 실행이 끝난 컨텍스트는 스택에서 pop

5. Global EC 제거 (pop)
   
   ⇒ 프로그램 종료

## 어휘적 범위 (LS; Lexical Scope)

> 함수를 선언한 위치에 따라 this가 결정되는 것
> 
> *호출 위치에 따라 this가 결정되는 Dynamic Scope와는 다르다*

- JS 함수들은 기본적으로 Lexical Scope를 따른다

```javascript
var name = '홍길동';

function wrapper() {
    var name = '이순신';
    getName();
}
function getName() {
    console.log(name);
}

wrapper(); // '홍길동'; (getName호출 위치와 무관)
getName(); // '홍길동';
```

## 주의

1. 함수 표현식은 Hoisting 되지 않습니다
   
   ```javascript
   func(); // Type Error 발생 : func가 undefined이기 때문
   
   var func = function() {
       console.log('실행 성공');
   }
   ```

    2. Lexical Environment는 직접 조작할 수 없는 이론상의 객체입니다

## 참고자료

[[Javascript] Execution Context와 Lexical Environment](https://iamsjy17.github.io/javascript/2019/06/10/js33_execution_context.html) *by Jewoo.Song*

[Lexical Environment 와 Closure에 대한 이해](https://velog.io/@paulkim/e) *by paulkim*

[[JS] 실행 컨텍스트, Lexical Environment & 호이스팅](https://velog.io/@wldns12378/JS-%EC%8B%A4%ED%96%89-%EC%BB%A8%ED%85%8D%EC%8A%A4%ED%8A%B8-Lexical-Environment-%ED%98%B8%EC%9D%B4%EC%8A%A4%ED%8C%85) *by wldns12378*

[[JS]Execution Context와 Call Stack](https://dkje.github.io/2020/08/30/ExecutionContext/#1-reference-to-the-outer-environment)  *by Dev X*

[변수의 유효범위와 클로저](https://ko.javascript.info/closure)  *모던 JavaScript 튜토리얼*
