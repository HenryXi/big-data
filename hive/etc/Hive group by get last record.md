# Hive group by get last record
Let's say you have a table like following.

Table A
```
id  timestamp   name
1   1621862007  henry
1   1621862001  henry
2   1621862016  justin
2   1621862018  justin
3   1621862002  matthew
3   1621862001  matthew
```

You want get following result.
```
id  timestamp   name
1   1621862007  henry
2   1621862018  justin
3   1621862002  matthew
```

The sql is like this.
```
with temp as(
    select id,max(timestamp) from A group by id
)
select A.* from A left join temp on A.id = temp.id and A.timestamp = temp.timestamp
```

EOF