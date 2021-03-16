MySQLの前提<br>
ポイント<br>
偶奇判定：mod関数<br>
重複排除：select distinct<br>
行数カウント：select count(XX)<br>
重複排除して行数カウント：select count(distinct XX)<br>
selectの中で四則演算して出力できる<br>
selectの中で複数列を入れるときはカンマで区切る<br>
並べ替え：fronの後にorder by XX、昇順はasc、降順はdesc<br>
1つのSQLが終わったらセミコロンで区切る<br>


## Revising the Select Query I
![image](https://user-images.githubusercontent.com/46245101/110939432-c0ddaf00-8378-11eb-8954-8cc3de9ef985.png)
```
select *
from CITY
where POPULATION >100000 and COUNTRYCODE = 'USA'
```

## Revising the Select Query II
![image](https://user-images.githubusercontent.com/46245101/110939564-f71b2e80-8378-11eb-9ff0-3653add498d2.png)
```
select NAME
from CITY
where POPULATION > 120000 and COUNTRYCODE = 'USA'
```

## Select By ID
![image](https://user-images.githubusercontent.com/46245101/110998454-2e61fd80-83c2-11eb-84e8-7e13b7fb3439.png)
```
select *
from CITY
where ID = 1661
```

## Weather Observation Station 1
![image](https://user-images.githubusercontent.com/46245101/111091997-103dfe00-8578-11eb-8e78-21c5160ba23b.png)
```
select CITY, STATE
from STATION
```
## Weather Observation Station 3
![image](https://user-images.githubusercontent.com/46245101/111092232-d28da500-8578-11eb-86f8-1094b7a0dc87.png)
```
select distinct CITY
from STATION
where mod(ID,2)=0
```

## Weather Observation Station 4
![image](https://user-images.githubusercontent.com/46245101/111235942-0fb76d00-8635-11eb-9b88-3606da0edf34.png)
```
select count(CITY) - count(distinct CITY)
from STATION
```

## Weather Observation Station 5
![image](https://user-images.githubusercontent.com/46245101/111237202-f663f000-8637-11eb-9513-a1ccf1bf7d8a.png)

```
select CITY, LENGTH(CITY) as length
from STATION
order by length asc, CITY asc
limit 1;

select CITY, LENGTH(CITY) as length
from STATION
order by length desc, CITY asc
limit 1;
```
