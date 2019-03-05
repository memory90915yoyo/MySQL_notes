# MySQL 筆記 #


## 前置 ##

安裝MySQL Community Server 8.0.15 (https://dev.mysql.com/downloads/mysql/)
和 圖形管理用的MySQL Workbench 8.0.15 (https://dev.mysql.com/downloads/workbench/)
注意：版本不一樣，可能會不能連接！！


下載 教學用的SQL script檔案 （http://books.gotop.com.tw/download/AED002900）
File->Open SQL Script 找cmdev.sql 和 world.sql 
然後執行 Query->Execute(All or Selection) 把資料給讀取進去 

於是到左邊工具欄 refresh all 就會出現兩個資料庫








## 基礎查詢 ##
![image](http://www.codedata.com.tw/wp-content/uploads/2013/12/mysql_03_snap_10.png)

查詢world資料庫的 city表格
```
USE world
SELECT * FROM city

或者
SELECT * FROM world.city

```


查詢要看的欄位就好 這邊看ID和 Name
```
SELECT ID, Name FROM world.city

```


可將查詢結果馬上計算 產生新欄位喔!

```
例如說要查月薪 乘上12變成年薪
SELECT ename, salary, salary*12 FROM cmdev.emp

```

欄位命名 使用AS
```
命名為月薪 年薪
SELECT ename, salary AS MonthSalary,
salary * 12 AS AnnualSalary 
FROM cmdev.emp

```

條件查詢 使用WHERE
```
只回傳人口小於900的資料
SELECT *
FROM world.city
WHERE Population < 900

```
```
只回傳 '台灣'的資料
SELECT *
FROM world.city
WHERE CountryCode = 'TWN'

```
```
其他可以搭配的

比較運算子有 = <=> != < > >=
邏輯運算子有  NOT && AND || OR XOR

```

條件查詢 其他例子
```
SELECT *
FROM world.city
WHERE Population > 80000 AND Population < 90000

```
```
SELECT *
FROM world.city
WHERE Population BETWEEN 80000 AND 90000

```
```
SELECT *
FROM world.city
WHERE CountryCode = 'TWN' OR
               CountryCode = 'USA' OR
               CountryCode = 'JPN' OR
               CountryCode = 'KOR' 
等同於
SELECT *
FROM world.city
WHERE CountryCode  in ('TWN', 'USA', 'JPN', 'KOR')

```
```
查詢 NULL 不能用 ＝  要用 ＩＳ 或者 <=> 
例如要查 沒有平均壽命的國家

SELECT Name , LifeExpectancy
FROM world.country
WHERE LifeExpectancy IS NULL

```

任意字串 使用like
```
％代表多個任意字元


SELECT Name 
FROM world.city
WHERE Name LIKE 'w%'


```
```
＿代表 一個任意字元

SELECT Name 
FROM world.city
WHERE Name LIKE '__w%'

```

排序 使用ORDER BY [ASC|DESC]
```
ASC 表示由小到大 為預設值

SELECT CountryCode, Name
FROM world.city
ORDER BY CountryCode ASC
```
```
DESC 表示由大到小

SELECT CountryCode, Name
FROM world.city
ORDER BY CountryCode DESC

```
```
可直接使用運算後的資料排序

SELECT ename, salary * 12 AS AnnualSalary 
FROM cmdev.emp
ORDER BY AnnualSalary

```

限制查詢數量
```
LIMIT 4 ＝ 只傳前4筆資料

SELECT empno, ename
FROM cmdev.emp
LIMIT 4


```
```
LIMIT 4, 2 = 跳過前4筆資料 回傳後2筆資料

SELECT empno, ename
FROM cmdev.emp
LIMIT 4, 2

```
```
於是 月薪前三名 就是...

SELECT empno, ename, salary
FROM cmdev.emp
ORDER BY salary DESC
LIMIT 3

```

排除重複資料 使用 ALL | DISTINCT 
```
ＡＬＬ ＝ 預設值 全部資料都回傳


SELECT ALL Continent FROM world.country


```
```
ＤＩＳＴＩＮＣＴ ＝ 重複的只傳一次


SELECT DISTINCT Continent FROM world.country

```



## 運算式＆函式 ##

...
```


```

...
```


```
...
```


```

...
```


```

...
```


```

...
```


```
