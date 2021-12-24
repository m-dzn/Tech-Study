# 프로토타입

## 구성

**생성자**

- prototype: 프로토타입 원형을 가리킴

**프로토타입 원형**

- constructor: 생성자를 가리킴

**프로토타입 인스턴스**

- \_\_proto\_\_ : 프로토타입 원형을 가리킴



## 특징

1. 프로토타입 체인
   
   : 상속된 프로토타입을 거슬러 올라가며 속성을 탐색

2. 최상위 프로토타입 = Object



## 사용법

### 관계 설정

1) ES5

```javascript
function Parent(prop) {
    this.prop = prop;
}

function Child(prop) {
    this.__proto__.constructor(prop);
}

Object.setPrototypeOf(Child.prototype, Parent.prototype);
```

2) ES6+

```javascript
class Parent {
    constructor(prop) {
    this.prop = prop;
    }
}

class Child extends Parent {
    constructor(prop) {
        super(prop);
    }
}
```
