# **FIELD()**

## **函数说明**

`FIELD()` 函数返回第一个字符串 `str` 在字符串列表 (str1,str2,str3,...) 中的位置。

## **语法说明**

```
> FIELD(str,str1,str2,str3,...)
```

## **参数释义**

|  参数   | 说明  |
|  ----  | ----  |
| str | 必要参数。要在列表中查找的值，且不区分大小写。 |
| str1,str2,str3,... | 必要参数。被搜索的列表中的各个元素，且不区分大小写。 |

## **返回值**

如果 `FIELD()` 的所有参数都是 string 类型，则所有参数都作为 string 类型进行比较。如果所有参数都是数字，则将它们作为数字进行比较。如果所有参数都是 double 类型，则将它们作为 double 类型进行比较。

- 如果在列表中找到指定的值，`FIELD()` 函数返回对应的位置索引。`FIELD()` 函数返回的索引的值从 1 开始。

- 如果在列表中找到多个指定的值，`FIELD()` 函数只返回第一个的索引值。

- 如果在列表中找不到指定的值，`FIELD()` 函数返回 0。

- 如果要查找的值为 `NULL`，`FIELD()` 函数返回 0。

## **示例**

- 示例 1：

```sql
mysql> SELECT FIELD('Bb', 'Aa', 'Bb', 'Cc', 'Dd', 'Ff');
+-------------------------------+
| field(Bb, Aa, Bb, Cc, Dd, Ff) |
+-------------------------------+
|                             2 |
+-------------------------------+
1 row in set (0.00 sec)

mysql> SELECT FIELD('Gg', 'Aa', 'Bb', 'Cc', 'Dd', 'Ff');
+-------------------------------+
| field(Gg, Aa, Bb, Cc, Dd, Ff) |
+-------------------------------+
|                             0 |
+-------------------------------+
1 row in set (0.00 sec)
```

- 示例 2：

```sql
drop table if exists t;
create table t(
    i int,
    f float,
    d double
);
insert into t() values (1, 1.1, 2.2), (2, 3.3, 4.4), (0, 0, 0), (0, null, 0);

mysql> select * from t;
+------+------+------+
| i    | f    | d    |
+------+------+------+
|    1 |  1.1 |  2.2 |
|    2 |  3.3 |  4.4 |
|    0 |    0 |    0 |
|    0 | NULL |    0 |
+------+------+------+
4 rows in set (0.01 sec)

mysql> select field(1, i, f, d) from t;
+-------------------+
| field(1, i, f, d) |
+-------------------+
|                 1 |
|                 0 |
|                 0 |
|                 0 |
+-------------------+
4 rows in set (0.01 sec)

mysql> select field(i, f, d, 0, 1, 2) from t;
+-------------------------+
| field(i, f, d, 0, 1, 2) |
+-------------------------+
|                       4 |
|                       5 |
|                       1 |
|                       2 |
+-------------------------+
4 rows in set (0.01 sec)

mysql> select field('1', f, d, 0, 1, 2) from t;
+-------------------------+
| field(1, f, d, 0, 1, 2) |
+-------------------------+
|                       4 |
|                       4 |
|                       4 |
|                       4 |
+-------------------------+
4 rows in set (0.01 sec)
```