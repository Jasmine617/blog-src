+++
author = "Jasmine"
title = "最常用的MySQL语句"
date = "2022-03-30"

description = "SQL"
tags = [
    "MySQL",
]

categories = [
    "CS",
   ]

+++

整理MySQL最常用的SQL语句（建表、增删改查数据）。更多的命令可参考：https://www.runoob.com/mysql/mysql-select-database.html

<!--more-->

## 常用命令

执行下列SQL语句前，请参照上节内容登录MySQL环境。

1. 选择数据库（上节已创建数据库mypython）。
   
   ```mysql
   mysql> use mypython;
   ```
   
   系统提示“Database changed”代表操作成功。
   
2. 查看系统中默认的表。

   在我们创建数据库时，系统会默认创建一些表。使用如下命令可查看。

   ```mysql
   mysql> show tables;
   ```

   

3. 使用create table语句，创建自己的表。

   下例的表名为students_info，他有id，name，gender，class四个字段，其中id为主键。

   ```mysql
   mysql> create table students_info(
   id varchar(10) not null ,
   name varchar(10) not null,
   gender varchar(10),
   class int,
   primary key (id)
    );
   ```

   下例的表名为test_scores，他有id，student_id，subject，score，submit_date四个字段，id为主键，且为自增长字段，即每次插入数据时自动加1。

   ```mysql
   mysql> create table test_scores(
   id int not null  auto_increment,
   student_id varchar(10) not null ,
   subject varchar(10) not null,
   score int not null,
   submit_date Date,
   primary key  (id)
    );
   ```

   创建完毕，可以重复步骤2的命令（show tables），检查是否创建成功。

   

4. 使用insert语句，向表中插入记录。

   ```mysql
   mysql> insert into students_info ( id, name,gender,class ) VALUES  ('20220101', 'Alice', 'female',9 );
   ```

   ```mysql
   mysql> insert into test_scores ( student_id, subject, score, submit_date ) VALUES  ('20220101', 'math', 99, now() );
   ```

   上述语句只是样例，可以根据需要为每个表插入多条记录。只要符合字段数据类型要求即可（主键必须唯一，字段的数据类型必须匹配等）。

   ```mysql
   mysql> insert into students_info ( id, name,gender,class ) VALUES  ('20220102', 'Nancy', 'female',10 );
   
   mysql> insert into test_scores ( student_id, subject, score, submit_date ) VALUES  ('20220102', 'math', 90, now() );
   mysql> insert into test_scores ( student_id, subject, score, submit_date ) VALUES  ('20220102', 'physics', 92, now() );
   mysql> insert into test_scores ( student_id, subject, score, submit_date ) VALUES  ('20220102', 'chemistry', 92, now() );
   ```

   

5. 使用select语句查询表中的记录。

   查询所有的学生信息（所有记录的所有字段）：

   ```mysql
   mysql> select * from students_info;
   ```

   查询所有学生的姓名（即所有记录的name字段）：

   ```mysql
   mysql> select name from students_info;
   ```

   查询id为20220101的学生姓名和班级（有查询条件，使用where）：

   ```mysql
   mysql> select name, class from students_info where id='20220101';
   ```

   查询数学成绩，并按照分数高低排序（使用order by，DESC代表降序）：

   ```mysql
   mysql> select * from test_scores where subject='math' order by score DESC;
   ```

   查询数学成绩高于95的人数（where后包含多个条件，统计数量用count()函数）：

   ```mysql
   mysql> select count(*) from test_scores where subject='math' and score>95;
   ```

   查询学生ID、学生姓名、班级和数学成绩，并按照分数高低排序（两表合并查询）：

   ```mysql
   mysql> select a.id, a.name, a.class, b.score from students_info a, test_scores b where a.id=b.student_id and b.subject='math' order by b.score DESC;
   ```

   

6. 使用update语句修改表中的记录。

   修改id为20220101的学生班级：

   ```mysql
   mysql> update students_info set class=12 where id='20220102';
   ```

   与select类似，update语句同样支持一次修改多个字段的值，以及在where后使用多个条件。

   

7. 使用delete删除表中的记录。

   ```mysql
   mysql> delete from  test_scores where subject='chemistry';
   ```

   



   
