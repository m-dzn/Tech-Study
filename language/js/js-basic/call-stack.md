# 콜 스택

> 호출된 함수의 실행 컨텍스트가 저장되는 후입선출(LIFO)형 자료구조

## 특징

### Run-to-completion

> 콜 스택을 모두 비운 후에야 다음 콜백 함수를 처리하는 JS Engine의 행태

## 작동 순서

1. 함수 호출 → 실행 컨텍스트 생성

2. 콜 스택 최상단에 1의 실행 컨텍스트 추가

3. 맨 위에서부터 함수 실행

4. 함수 종료 시 해당 함수의 실행 컨텍스트 제거

5. 다음 함수 실행
