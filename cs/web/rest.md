# REST API

> **Representational State Transfer**
> 자원을 이름 (컬렉션) 으로 구분하여 상태를 주고 받는 전송 방식을 말합니다.

## 특징

1. JSON, XML 형식으로 데이터를 전송합니다.

2. HTTP URI는 요청할 자원을 명시합니다.

3. HTTP Method는  자원에 대한 CRUD 동작을 기술합니다. <br>

## REST에 사용되는 HTTP Method의 종류

| CRUD Method | HTTP Method |
|:-----------:|:-----------:|
| CREATE      | POST        |
| READ        | GET         |
| UPDATE      | PUT, PATCH  |
| DELETE      | DELETE      |

+&nbsp;HEAD : 헤더 정보를 조회하기 위한 메서드

## 용어

> **컬렉션 (Collection)**
>
> 여러 다큐먼트 (Document) 또는 객체 들의 집합, 복수
> 서버측에서 식별자 및 리소스 URL을 생성 & 관리

> **다큐먼트 (Document)**
> 
> 객체, 단수

> **컨트롤 URL**
>
> CRUD + HEAD 로는 표현할 수 없는 동작을 수행하기 위한 URL로
> 리소스 뒤에 동사를 넣어 표현

> **스토어 (Store)** 
>
> 클라이언트측에서 식별자를 생성 & 관리하는 리소스 URL
> 서버측의 컬렉션과 대응되는 개념

## 구성

**리소스**

    식별자 (id) 를 가지고 있는 컬렉션

    (※ 컬렉션이란?  동일한 종류, 여러 다큐먼트의 집합)

**메서드**

    4가지 HTTP Method

**메세지**

    JSON, XML 등의 데이터

## 작성 규칙

1. 컬렉션을 표현할 때는 복수형 명사를 사용

2. 
