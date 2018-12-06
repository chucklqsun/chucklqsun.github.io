### issue "--secure-file-priv"
change /usr/local/etc/my.cnf
```
[mysqld_safe]
[mysqld]
secure_file_priv=""
```

### Cheatsheet
#### Querying Data:
1. SELECT column as new_column, column2…. FROM table WHERE condition ORDER BY column ASC [DESC], column2 ASC [DESC],...;
2. SELECT DISTINCT (column) FROM table;
3. SELECT column1 , column2…. FROM table1 LEFT JOIN table2 on condition WHERE condition;
4. SELECT COUNT (\*) FROM table
5. SELECT * FROM table GROUP BY column_1, column_2, ... HAVING condition;

#### Modifying Data
1. INSERT INTO table(column1,column2,...) VALUES(value_1,value_2,...), (value_1,value_2,...), (value_1,value_2,...)...

#### Updating Data
1. UPDATE table SET column_1 = value_1, ... WHERE condition
2. UPDATE table_1, table_2 INNER JOIN table_1 ON table_1.column_1 = table_2.column_1 SET column_1 = value_1, WHERE condition

#### Unique
CREATE UNIQUE INDEX index_name ON table_name(index_column_1,index_column_2,...);

#### Index
CREATE INDEX idx_name ON table(column_name);
