# Sequelize

## MySQL과 비교

| MySQL    | Sequelize        |
| -------- | ---------------- |
| VARCHAR  | String           |
| INT      | INTEGER          |
| TINYINT  | BOOLEAN          |
| DATETIME | DATE             |
| UNSIGNED | UNSIGNED         |
| DEFAULT  | defaultValue:    |
| now()    | Sequelize.NOW    |
| NOT NULL | allowNull: false |
| UNIQUE   | unique: true     |
|          |                  |

## 관계 정의

| 메서드         | 관계         |
| -------------- | ------------ |
| .hasMany       | 1:N 또는 1:1 |
| .belongsTo     | N:1 또는 1:1 |
| .belongsToMany | N:M          |
|                |              |

## Op 객체

Op.lt : < 작음
Op.lte : ≤ 작거나 같음
Op.gte : ≥ 크거나 같음
Op.gt : > 큼

Op.ne : 같지 않음
Op.or : 또는
Op.in : 목록 중 하나
Op.notIn : 목록 제외

## CLI 명령어

### MySQL DataBase 생성

```shell
npx sequelize db:create
```



## Sequelize의 메서드

.build( ) : 메모리에 인스턴스를 생성하는 메서드

.save( ) : .build( )로 생성된 인스턴스를 DB에 저장하는 메서드

.create( ) : 위의 .build( )와 .save( )를 동시에 수행하는 메서드

.destroy({ where: { id: 1 } }) : 특정 레코드를 삭제하는 메서드