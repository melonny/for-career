## Databases
### Important Topics
1. [What Is Mysql](./mysql/whatIsMysql.md)
2. [InnoDB](./mysql/InnoDB.md)
### Tips for Mysql
##### 1. Window Function
```A Window Function, also known as an OLAP function (Online Analytical Processing), allows for real-time analysis of data in a database.```

```The basic syntax of a Window Function is as follows:```

```sql
<Window Function> over (partition by <column used for grouping>
                  order by <column used for sorting>)
```
    The <Window Function> can be one of the following two types of functions:
    a)Specialized Window Functions, such as rank, dense_rank, and row_number.
    b)Aggregate Functions, such as sum, avg, count, max, and min.
```Because Window Functions operate on the results of the where or group by clauses, they are generally only used in the select clause.```
