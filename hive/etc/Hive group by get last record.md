# Hive group by get last record
Let's say you have a table like following.

Table A
```
id  timestamp
1   1621862007
1   1621862001
2   1621862016
2   1621862018
3   1621862002
3   1621862001
```

You want get following result.
```
id  timestamp
1   1621862007
2   1621862018
3   1621862002
```

The sql is like this.
```
with temp as(
    select id,max(timestamp) from A group by id
)
select * from A left join temp on A.id = temp.id and A.timestamp = temp.timestamp
```

EOF