MySQLの前提

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
