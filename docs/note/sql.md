# SQL
- case
```
update salary 
set 
    sex = case sex
        when 'm' then 'f'
        else 'm'
    end;
```

- 剰余
    - `mod` の方が `%` よりはやい
    - 例: [LeetCode](https://leetcode.com/problems/not-boring-movies)
```
SELECT
    *
FROM
    cinema
WHERE
    id % 2 = 1
    AND description != 'boring'
ORDER BY
    rating DESC;
```

- group by 結果に対しての条件は having を使用
```
SELECT
    class
FROM
    courses
GROUP BY
    class
HAVING
    count(DISTINCT student) >= 5;
```

- `DATE` 型の演算の注意点
```
select to_date('2015-01-31', 'YYYYMMDD')+1 date;
    date    
------------
 2015-01-02
```

## PostgreSQL
- テーブルのレコード全削除
```
DELETE FROM table_name;
```