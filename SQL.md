# SQL
## JOIN
Use join to look for data across tables, associate data across tables
- Inner join looks for data that overlaps
- LEFT JOIN is outer join, returns values in left table even if matching data on right table doesnt exist
- RIGHT JOIN is same, but switch left and right
- FULL OUTER JOIN returns combination of left and right join results
    - Note MYSQL doesnt supper full outer join


```SQL
SELECT people.first_name, people.state, states.division 
FROM people
JOIN states          //people and states are our two tables
ON people.state=states.state_abbrev;
```
this returns the first names, state in the people table and states division in the states table if people.state = states.state_abbrev 

## GROUPBY






# BIG DATA 

- Massive amounts of data which cannot be stored, processed, analyzed in traditional ways
- Hadoop is a solution to big data problems
    - A framework that manages big data storage in a distributed way and processes it in parallel
    - Hadoop Distributed File System, hadoop reads and writes files to HDFS
- Hadoop and Spark are both big data processing frameworks