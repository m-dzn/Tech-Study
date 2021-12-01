# 동기-비동기와 블로킹-논블로킹



## 구분

**동기-비동기**

    서로 다른 앱이나 작업 간의 결과 확인 여부로 결정

    ( **동기** : 결과 반환됐나 계속 확인 )

    ( **비동기** : 알아서 하겠지~ 확인 x )



**블로킹-논블로킹**   

    하나의 앱에서 함수 간의 작업 제어권 반환 여부로 결정

    ( **블로킹** : 제어권 반환, 기다림 )

    ( **논블로킹** : 제어권 반환 x, 안 기다림 )



<br>



## 조합

1. 동기: 결과 나왔나 계속 확인하면서
       
   
   1-1. Blocking → 할 일 안 하고 기다리기 (ex: 위에서 아래로 짠 보통 코드)
   
   1-2. Non Blocking → 작업 계속하기 (ex: 딴 짓하면서 결과 반환을 기다리는 while문)
   
           ※ 다른 작업을 병행하지만, 요청한 결과가 반환되기 전에는
   
               호출한 함수의 작업이 완료되지 않습니다.



2. 비동기: 결과는 신경도 안 쓰고 다른 데 (콜백 함수나 Promise 등에게) 위임해버린 뒤
   
   
   
   2-1. Blocking → 할 일 안 하고 기다리기 (ex: Node.js + MySQL 또는 Java + JDBC)
   
           ※ 동기-Blocking을 쓴 것과 비슷한 결과를 얻기 때문에 일부러 쓰지는 않습니다.
   
   2-2. Non Blocking → 작업 계속하기  (ex: AJAX, 흔히 말하는 비동기 처리)
   
           ※ 다른 작업을 병행하며, 병행 작업이 모두 끝나면 요청한 결과 반환과 상관 없이
   
           호출한 함수의 작업이 완료됩니다.



