# **LIKE**

## **语法说明**

LIKE 操作符用于在 WHERE 子句中搜索列中的指定模式。

有两个通配符经常与 LIKE 操作符一起使用：

* 百分号 (%) 代表了 0、1 或多个字符。
* 下划线 (_) 代表单个字符。

## **语法结构**

```
> SELECT column1, column2, ...
FROM table_name
WHERE columnN LIKE pattern;
```

## **示例**

```sql
mysql> SELECT * FROM Customers
WHERE CustomerName LIKE 'a%'; //The following SQL statement selects all customers with a CustomerName starting with "a"

mysql> SELECT * FROM Customers
WHERE CustomerName LIKE '%a'; //The following SQL statement selects all customers with a CustomerName ending with "a"

mysql> SELECT * FROM Customers
WHERE CustomerName LIKE '%or%'; //The following SQL statement selects all customers with a CustomerName that have "or" in any position

mysql> SELECT * FROM Customers
WHERE CustomerName LIKE '_r%'; //The following SQL statement selects all customers with a CustomerName that have "r" in the second position

mysql> SELECT * FROM Customers
WHERE CustomerName LIKE 'a__%'; //The following SQL statement selects all customers with a CustomerName that starts with "a" and are at least 3 characters in length

mysql> SELECT * FROM Customers
WHERE ContactName LIKE 'a%o'; //The following SQL statement selects all customers with a ContactName that starts with "a" and ends with "o"

mysql> SELECT * FROM Customers
WHERE CustomerName NOT LIKE 'a%'; //The following SQL statement selects all customers with a CustomerName that does NOT start with "a"
```
