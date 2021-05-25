# Hive case when example
Let's say you have table like following. You want to query the nums of each level.

Table A
```
id  name    score
1   henry   95
2   vivian  83
3   judy    63
4   justin  82
5   matthew 75
6   gerard  82
```

You what get this result.
```
total   level1  level2  level3
6	    1       1       4
```

The following sql can get the right result.
```
select count(*) as total,
  sum(case when score>=60 and score<70 then 1 else 0 end ) as level1,
  sum(case when score>=70 and score<80 then 1 else 0 end ) as level2,
  sum(case when score>=80 and score<100 then 1 else 0 end ) as level3
from scores
```