# 계층형 DB 구조

## 참고 자료

[Models for Hierarchical Data](https://www.slideshare.net/billkarwin/models-for-hierarchical-data?next\_slideshow=1\&fbclid=IwAR0qhouJFaND4Fi\_i5V2lAUxwot1xREfJxmjw\_JGOhGw9J3l98z0F1fIUw8)

[Camel's Note :: tree 구조를 mysql 에 저장하기, hierarchy, closure table 을 mysql에 저장하자](https://blog.yevgnenll.me/posts/save-tree-in-mysql-closure-pattern-hierarchy-structure)

## 1. Adjacency List

* 자식 노드가 부모 노드의 id를 속성으로 갖습니다.
* 쉽게 생각해 적용할 수 있습니다.

| id | parent\_id | name | comment                                          |
| -- | ---------- | ---- | ------------------------------------------------ |
| 1  | NULL       | 생물   | 생명을 가지고 스스로 생활 현상을 유지하여 나가는 물체                   |
| 2  | 1          | 식물   | 풀, 나무와 같은 스스로의 힘으로 움직일 수 없는 생명체                  |
| 3  | 1          | 동물   | 생물계의 두 갈래 가운데 먹이로 영양분을 얻고 자유롭게 몸을 움직일 수 있는 생물    |
| 4  | 3          | 쥐    | 사람의 집 근처 어두운 곳에서 살며 몸은 진한 회색에 긴 꼬리를 가지고 있는 작은 동물 |
| 5  | 3          | 참새   | 주로 사람이 사는 곳 근처에 살며, 몸은 갈색이고 배는 회백색인 작은 새         |

### 이동

```sql
UPDATE Creature
SET parent_id = 이동할_부모id
WHERE id = 이동할_노드id
```

### 얕은 탐색

```sql
# 자식 노드 탐색
SELECT *
FROM Creature c1
LEFT JOIN Creature c2
ON (c2.parent_id = c1.id);

# 부모 노드 탐색
SELECT *
FROM Creature c1
JOIN Creature c2
ON (c1.parent_id = c2.id);
```

### 깊은 탐색

```sql
# 깊은 자식 탐색
SELECT * FROM Creature c1
    LEFT JOIN Creature c2 ON (c2.parent_id = c1.id)
    LEFT JOIN Creature c3 ON (c3.parent_id = c2.id)
    LEFT JOIN Creature c4 ON (c4.parent_id = c3.id)
    LEFT JOIN Creature c5 ON (c5.parent_id = c4.id)
    LEFT JOIN Creature c6 ON (c6.parent_id = c5.id)
    ...
```

## 2. Breadcrumbs

> 파일 시스템의 방식 채용

### 단점

* 경로 길이가 제한될 수 밖에 없습니다.

| id | path   | name | comment                                          |
| -- | ------ | ---- | ------------------------------------------------ |
| 1  | 1/     | 생물   | 생명을 가지고 스스로 생활 현상을 유지하여 나가는 물체                   |
| 2  | 1/2/   | 식물   | 풀, 나무와 같은 스스로의 힘으로 움직일 수 없는 생명체                  |
| 3  | 1/3/   | 동물   | 생물계의 두 갈래 가운데 먹이로 영양분을 얻고 자유롭게 몸을 움직일 수 있는 생물    |
| 4  | 1/3/4/ | 쥐    | 사람의 집 근처 어두운 곳에서 살며 몸은 진한 회색에 긴 꼬리를 가지고 있는 작은 동물 |
| 5  | 1/3/5/ | 참새   | 주로 사람이 사는 곳 근처에 살며, 몸은 갈색이고 배는 회백색인 작은 새         |

### 삽입

```sql
INSERT INTO Creature(name, comment)
VALUES ('개', '인간을 잘 따라 애완, 가축 등의 목적으로 기르는 동물');

UPDATE Creature
SET path = $parent_path || LAST_INSERT_ID() || '/'
WHERE id = LAST_INSERT_ID();
```

### 탐색

```sql
# 후손 탐색
SELECT * FROM Creature
WHERE path LIKE '1/3/%';    # 동물 노드의 모든 후손 노드 탐색

# 조상 탐색
SELECT * FROM Creature
WHERE '1/3/4/' LIKE path || '%';    # 참새 노드의 모든 조상 노드 탐색
```

## 3. Nested Sets

## 4. Closure Table

* 계층 간의 관계를 다른 테이블에서 관리합니다. (JPA의 연결 테이블티 전략과 유사)

### 장점

* 조상, 자손 조회가 간편합니다.
* 데이터 삽입/삭제가 용이합니다.

### 단점

* 별도 테이블을 만들기 때문에 저장공간을 많이 차지합니다.

| id | name | comment                                          |
| -- | ---- | ------------------------------------------------ |
| 1  | 생물   | 생명을 가지고 스스로 생활 현상을 유지하여 나가는 물체                   |
| 2  | 식물   | 풀, 나무와 같은 스스로의 힘으로 움직일 수 없는 생명체                  |
| 3  | 동물   | 생물계의 두 갈래 가운데 먹이로 영양분을 얻고 자유롭게 몸을 움직일 수 있는 생물    |
| 4  | 쥐    | 사람의 집 근처 어두운 곳에서 살며 몸은 진한 회색에 긴 꼬리를 가지고 있는 작은 동물 |
| 5  | 참새   | 주로 사람이 사는 곳 근처에 살며, 몸은 갈색이고 배는 회백색인 작은 새         |

| ancestor | descendant | depth |
| -------- | ---------- | ----- |
| 1        | 1          | 0     |
| 1        | 2          | 1     |
| 1        | 3          | 1     |
| 1        | 4          | 2     |
| 1        | 5          | 2     |
| 2        | 2          | 0     |
| 3        | 3          | 0     |
| 3        | 4          | 1     |
| 3        | 5          | 1     |
| 4        | 4          | 0     |
| 5        | 5          | 0     |

### 삽입

```sql
INSERT INTO Creature(id, name, comment) VALUES(6, '개', '귀여워');

INSERT INTO Creature_Closure(ancestor, descendant, depth)
    SELECT ancestor, 6, depth + 1
    FROM Creature_Closure
    WHERE descendant = 3
        UNION ALL
        SELECT 6,6;
```

### 조회

```sql
# 후손 탐색
SELECT c.*
FROM Creature AS c
     JOIN Creature_Closure AS clo ON c.id = clo.descendant
WHERE clo.ancestor = 3;

# 조상 탐색
SELECT c.*
FROM Creature AS c
     JOIN Creature_Closure AS clo ON c.id = clo.ancestor
WHERE clo.descendant = 3;
```

### 이동

```sql
##### 6을 root로 하는 subtree를 3의 밑으로 옮기기 #####

# 우선 이동할 노드의 계층 정보만 제거 (후손 정보는 유지)
DELETE FROM Creature_Closure
WHERE descendant IN (
     SELECT descendant
     FROM Creature_Closure
     WHERE ancestor = 6)
AND ancestor IN (
     SELECT ancestor
     FROM Creature_Closure
     WHERE descendant = 6
          AND ancestor != descendant);

# 삭제 과정에서 고아가 된 서브트리를 새 조상에 할당
## 후손이 3인 모든 (ancestor, descendant) 조합과
## 조상이 6인 모든 (ancestor, descendant) 조합을 카테시안 곱(CROSS JOIN)합니다.
INSERT INTO Creature_Closure(ancestor, descendant) 
     SELECT supertree.ancestor, subtree.descendant
     FROM Creature_Closure AS supertree
          CROSS JOIN Creature_Closure AS subtree
     WHERE supertree.descendant = 3
          AND subtree.ancestor = 6;
```

### 삭제

```sql
# 특정 노드 삭제 시 해당 노드의 계층 path 정보 제거
## 해당 id를 자손으로 갖는 행만 모두 제거
DELETE FROM Creature_Closure
WHERE descendant = 3;

DELETE FROM Creature
WHERE id = 3;

# 특정 노드 및 그 후손의 계층 path 정보 모두 제거
DELETE FROM Creature_Closure
WHERE descendant IN (
     SELECT descendant
     FROM Creature_Closure
     WHERE ancestor = 6);
```
