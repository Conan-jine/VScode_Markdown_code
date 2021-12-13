# 数据库的基本概念
1. 数据库的英文单词：DataBase 简称：DB
2. 什么是数据库？
   * 用于存储和管理数据的仓库  
3. 数据库的特点：
   1. 持久化存储数据。其实数据库就是一个文件系统
   2. 方便存储和管理数据
   3. 使用了统一的方式操作数据库
4. 常见的数据库软件
   * Oracle
   * MySQL
   * SQL service

# MySQL数据库软件
1. [安装、卸载教程](https://blog.csdn.net/pujun1201/article/details/119913745)
2. 配置环境变量 MYSQL_HOME %MYSQL_HOME%\bin

# SQL
1. 什么是SQL
   >Structured Query Language：结构化查询语言。  
   >其实就是定义了操作所有关系型数据库的规则。每一种数据库操作的方式存在不一样的地方，称为“方言”
2. SQL通用语法
   1. SQL 语句可以单行或多行书写，以分号结尾
   2. 可以使用空格和缩进来增强语句的可读性
   3. MySQL 数据库的 SQL 语句不区分大小写，关键字建议使用大写
   4. 3 种注释
      * 单行注释：-- 注释内容 或 # 注释内容(MySQL 特有)
      * 多行注释：/* 注释 */
3. SQL分类
   1. DDL(Data Definition Language)数据定义语言  
        
        >用来定义数据库对象：数据库，表，列等。关键字：create，drop，alter 等
   2. DML(Data Manipulation Language)数据操作语言  
        
        >用来对数据库中表的数据进行增删改。关键字：insert，delete，update 等
   3. DQL(Data Query Language)数据查询语言  
        
        >用来查询数据库中表的记录(数据)。关键字：select，where 等
   4. DCL(Data Control Language)数据控制语言(了解)  
        
        >用来定义数据库的访问权限和安全级别，及创建用户。关键字：GRANT，REVOKE 等
## DDL：操作数据库、表
1. 操作数据库
   1. Create
      * 创建数据库：
        
        >create databse 数据库名称；
      * 创建数据库，并指定字符集
        
        >create database 数据库名称 character set 字符集名；
      * 创建数据库，判断是否存在，并指定字符集为gbk
        
        >create database  if not exists 数据库名称 character set gbk；
   2. Retrieve
      * 查询所有数据库的名称：
        
        >show databases；
      * 查询某个数据库的字符集：查询某个数据库的创建语句
        
        >show create database 数据库名称；
   3. Update
      * 修改数据库的字符集
        
        >alter database 数据库名称 character set 字符集名称；
   4. Delete
      * 删除数据库
        
        >drop database 数据库名称；
      * 判断数据库是否存在，存在则删除数据库
        
        >drop database if exists 数据库名称；
   5. 使用数据库
      * 查询当前正在使用的数据库名称
        
        >select database();
      * 使用数据库
        
        >use 数据库名称；
2. 操作表
   1. Create
      1. 语法
         >create tabel 表名(  
         >   列名1 数据类型,   
         >   列名2 数据类型,   
         >   ···  
         >   列名n 数据类型n  
         >);
      2. 数据类型
         1. int
         2. double
         3. date, 只包含年月日, yyyy-mm-dd
         4. datetime, 包含年月日时分秒, yyyy-MM-dd HH:mm:ss
         5. timestamp, 时间戳类型 包含年月日时分秒( 如果将来不赋值, 自动获取当前时间 )
         6. varchar, 字符串
      3. 复制表
         
         > create table 表名 like 被复制的表名; 
   2. Retrieve
      * 查询某个数据库中所有的表名称
        
        >show tables；
      * 查询表结构
        
        >desc 表名；
   3. Update
      1. 修改表名
         
         >alter table 表名 rename to 新表名;
      2. 修改表的字符集
         
         >alter table 表名 character set 字符集名称;
      3. 添加一列
         
         >alter table 表名 add 列名 数据类型;
      4. 修改列的名称 类型
         >alter table 表名 change 列名 新列名 新数据类型;
         >alter table 表名 modify 列名 新数据类型;
      5. 删除列
         
         >alter table 表名 drop 列名;
   4. Delete
      >drop table 表名;  
      >drop table if exists 表名;

## DML : 增删改表中数据
1. 添加数据
   1. 语法
      
      >insert into 表名(列名1, 列名2, ... , 列名n) values(值1, 值2, ... ,值n);
2. 删除数据
   1. 语法
      
      >delete from 表名 [where 条件]
   2. 注意
      1. 如果不加条件, 则删除表中所有数据
      2. 如果要删除所有记录: TRUNCATE TABLE 表名;(先删除表, 然后再创建一张一模一样的表)
      3. 
3. 修改数据
   1. 语法
      
      >update 表名 set 列名1 = 值1, 列名2 = 值2, ... , [where 条件];
   2. 注意
      1. 如果不加任何条件, 则会将表中所有记录修改
## DQL : 查询表中的记录
1. 语法
   >select  
   >   字段列表  
   >from  
   >   表名列表  
   >where  
   >   条件列表  
   >group by  
   >   分组字段  
   >having  
   >   分组之后的条件  
   >order by  
   >   排序  
   >limit  
   >  分页限定
2. 基础查询
   1. 多个字段的查询
      
      >select 字段名1, 字段名2, 字段名3, ... from 表名;
   2. 去除重复
      
      >distinct
   3. 计算列
      * 一般可用四则运算计算一些列的值
      * ifnull(表达式1, 表达式2) : null 参与的运算, 计算结果都为null
        * 表达式1 : 哪个字段需要判断是否为null
        * 如果该字段为null后的替换值
   4. 起别名
      
      >as : as也可以省略
3. 条件查询
   1. where字句后跟条件
   2. 运算符
      >'*' > < <= >= = <>  
      BETWEEN...AND  
      IN(集合)  
      LIKE : 模糊查询 _:代表单个任意字符 %:多个任意字符 
      IS NULL  
      and 或 &&  
      or 或 ||  
      not 或 |  
4. 排序查询
   1. 语法
      
      >order by 排序字段1 排序方式, 排序字段2 排序方式2 ......;
   2. 排序方式
      >ASC : 升序, 默认的  
      >DESC : 降序
5. 聚合函数
   1. count : 计算个数
   2. max : 计算最大值
   3. min : 计算最小值
   4. sum : 计算和
   5. avg : 计算平均值
6. 分组查询
   1. 语法
      
      >group by 分组字段;
   2. 注意
      1. 分组之后查询的字段 : 分组字段 聚合函数
      2. where 和 having 的分别
         1. where 在分组之前进行限定, 如果不满足条件, 则不参与分组. having 在分组之后进行限定, 如果不满足结果, 则不会被查询出来
         2. where 后不可以跟聚合函数, having 可以进行聚合函数的判断.
7. 分页查询
   1. 语法 : limit 开始的索引, 每页查询的条数;
   2. 公式 : 开始的索引 = (当前的页码 - 1) * 每页显示的条数
   3. limit分页操作是MySQL的"方言"

## 约束
1. 概念: 对表中的数据进行限定, 保证数据的正确性, 有效性和完整性
2. 分类
   1. 主键约束: primary key
   2. 非空约束: not null
   3. 唯一约束: unique
   4. 外键约束: foreign key
3. 非空约束
   1. 创建表时添加约束
      >CREATE TABLE stu(
         id INT,
         name VARCHAR(20) NOT NULL
      );
   2. 创建表完后, 添加非空约束
      
      >ALTER TABLE stu MODIFY name VARCHAR(20) NOT NULL;
   3. 删除name的非空约束
      
      >ALTER TABLE stu MODIFY name VARCHAR(20);
4. 唯一约束
   1. 创建表时, 添加唯一约束
      >CREATE TABLE stu(
         id INT,
         phone_number VARCHAR(20) UNIQUE
      );
   2. 删除唯一约束
      
      >ALTER TABLE stu DROP INDEX phone_number;
   3. 在创建表后, 添加唯一约束
      
      >ALTER TABLE stu MODIFY phone_number VARCHAR(20) UNIQUE;
5. 主键约束
   1. 注意
      1. 含义: 非空且唯一
      2. 一张表只能有一个字段为主键
      3. 主键就是表中记录的唯一标识
   2. 在创建表时, 添加主键约束
      >CREATE TABLE stu(
         id INT PRIMARY KEY,
         name VARCHAR(20)
      );
   3. 删除主键
      
      >ALTER TABLE stu DROP PRIMARY KEY;
   4. 创建完表后, 添加主键
      
      >ALTER TABLE stu MODIFY id INT PRIMARY KEY;
   5. 自动增长
      1. 概念: 如果某一列时数值类型的, 使用auto_increment 可以用来完成值的自动增长
      2. 在创建表时, 添加主键约束, 并且完成主键自增长
         >CREATE TABLE stu(
            id INT PRIMARY KEY AUTO_INCREMENT,
            name VARCHAR(20)
         );
      3. 删除自动增长
         
         >ALTER TABLE stu MODIFY id INT;
      4. 添加自动增长
         
         >ALTER TABLE stu MODIFY id INT AUTO_INCREMENT;
6. 外键约束
   1. 在创建表时, 可以添加外键
      >CREATE TABLE 表名(
         ...,
         外键列,
         constraint 外键名称 foreign key (外键列名称) refernces 主表名称(主表列名称)
      )
   2. 删除外键
      
      >ALTER TABLE 表名 DROP FOREIGN KEY 外键名称;
   3. 创建表之后, 添加外键
      
      >ALTER TABLE 表名 ADD CONSTRAINT 外键名称 FOREIGN KET (外键字段名称) REFERENCES 主表名称(主表列名称);
   4. 级联操作
      1. 添加级联操作
         
         >ALTER TABLE 表名 ADD CONSTRAINT 外键名称 FOREIGN KEY (外键字段名称) REFERENCES 主表名称(主表列名称) ON UPDATE CASCADE ON DELETE CASCADE;
      2. 分类
         1. 级联更新: ON UPDATE CASCADE
         2. 级联删除: ON DELETE CASCADE
## 多表之间的关系
1. 分类
   1. 一对一
   2. 一对多, 多对一
   3. 多对多
2. 实现关系
   1. 一对多, 多对一
      * 实现方式: 在多的一方建立外键, 指向一的一方的主键
   2. 多对多
      * 实现方式: 借助第三张表, 作为中间表, 中间表至少包含两个字段, 均作为外键, 分别指向两张表的主键
   3. 一对一
      * 实现方式: 在任意一方添加唯一外键指向另一方的主键
## 范式

1. 概念

   设计数据库时，需要遵守的一些范式。

   > 设计关系数据库时，遵从不同的规范要求，设计合理的关系型数据库，这些不同的规范要求被称为不同的范式，各种范式呈递次规范，越高的范式数据库冗余越小。

2. 分类

   1. 第一范式（1NF）：每一列都是不可分割的原子数据项
   2. 第二范式（2NF）：在1NF的基础上，非码属性必须完全依赖于候选码（在1NF基础上消除非主属性对主码的部分函数依赖）
      * 函数依赖：如果通过A属性（属性组）的值，可以确定唯一B属性的值，则称B依赖于A
      * 完全函数依赖：如果A是一个属性组，则B属性值的确定需要依赖于A属性组中所有的属性值。
      * 部分函数依赖：如果A是一个属性组，则B属性值的确定只需要依赖于A属性组中某一些值即可。
      * 传递函数依赖：如果通过A属性（属性组）的值，可以确定唯一B属性的值，在通过B属性（属性组）的值可以确定唯一C属性的值，则称C传递依赖于A。
      * 码：一张表中，如果一个属性或属性组，被其他所有属性完全依赖，则称这个属性（属性组）为该表的码。
      * 主属性：码属性组中的所有属性
      * 非主属性：除过码属性组的属性
   3. 第三范式（3NF）：在2NF基础上， 任何非主属性不依赖于其他非主属性（在2NF基础上消除传递依赖）

## 数据库的备份和还原

1. 命令行：
   * 备份：mysqldump -u用户名 -p密码 数据库名 > 保存的路径
   * 还原：登录数据库，创建数据库，使用数据库，执行文件
2. 图形化工具

## 多表查询

1. 笛卡尔积
2. 多表查询的分类
   1. 内连接查询
      1. 隐式内连接：使用where条件消除无用数据
      2. 显示内连接：使用join和on
   2. 外连接查询
      1. 左外连接：使用left join和on
      2. 右外连接：使用right join和on
   3. 子查询：查询语句中嵌套查询
      1. 结果单行单列：作为条件，使用运算符去判断
      2. 结果多行单列：作为条件，使用IN运算符
      3. 结果多行多列：作为一张虚拟表参与查询

## 事务

1. 事务的基本介绍

   1. 概念：如果一个包含多个步骤的业务操作，被事务管理，那么这些操作一荣俱荣一损俱损
   2. 操作
      1. 开启事务：start transaction；
      2. 回滚：rollback；
      3. 提交：commit；
   3. MySQL默认一条DML语句会自动提交一次事务
      1. 事务提交的两种方式
         1. 自动提交
         2. 手动提交
      2. 修改事务的默认提交方式
         1. 查看事务的默认提交方式：select @@autocommit；1代表自动提交，0代表手动提交
         2. 修改默认提交方式：set @@autocommit = 0；

2. 事务的四大特征

   1. 原子性：是不可分割的最小操作单位，要么同时成功，要么同时失败
   2. 持久性：当事务提交或回滚后，数据库会持久化的保存数据
   3. 隔离性：多个事务之间，相互独立
   4. 一致性：事务操作前后，数据总量不变

3. 事务的隔离级别

   1. 概念：多个事务之间隔离，相互独立。但如果多个事务操作同一批数据，则会引发一些问题，设置不同的隔离级别就可以解决这些问题
   2. 存在问题：
      1. 脏读：一个事务，读取到另一个事务中没有提交的数据
      2. 不可重复读：在同一个事务中，两次读到的数据不一样
      3. 幻读：一个事务操作（DML）数据表中所有记录，另一个事务添加了一条数据，则第一个事务查询不到自己的修改
   3. 隔离级别：级别越高效率越低
      1. read uncommitted：读未提交（产生三种问题）
      2. read committed：读已提交（不可重复读、幻读）
      3. repeatable read：可重复读（幻读）
      4. serialization：串行化
   4. 隔离查询：select @@tx_isolation；
   5. 隔离设置：set global transaction isolation level 级别字符串；

   ## DCL

   1. 管理用户
      1. 添加用户：create user ‘用户名‘@’主机名‘ identified by ’密码‘
      2. 删除用户：drop user ’用户名‘@’主机名‘
      3. 修改用户密码：update user set password = password(’新密码‘) where user = '用户名' 或者 set password for ‘用户名’@‘主机名’ = password('新密码')
      4. 查询用户：切换到数据库，select * from user；
   2. 授权
      1. 查询权限：show grants for ‘用户名’@‘主机名’
      2. 授予权限：grant 权限列表 on 数据库名.表名 to ‘用户名’@‘主机名’
      3. 撤销权限：revoke 权限列表 on 数据库名.表名 from ‘用户名’@‘主机名’