# Hive not in example
We can use `left join` in Hive to implements `in` or `not in` operation. Now we have two tables A and B like following.

Table A
```
id  name
1   henry
2   justin
3   matthew
```

Table B
```
id  login_time
1   1
2   3
6   5
```

Let's say you want query people in Table A and **NOT IN** Table B. The sql is like this.
```
select A.id from A left join B on A.id = B.id where B.id is null.
```

If you want query people in Table A and **IN** Table B. The sql is like this.
```
select A.id from A left join B on A.id = B.id where B.id is not null.
```


EOF


