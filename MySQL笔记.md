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
# DDL：操作数据库、表
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

# DML : 增删改表中数据
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
# DQL : 查询表中的记录
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

# 约束

# 多表之间的关系

# 范式

# 数据库的备份和还原