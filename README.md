# notes-sql-hive-  
Hive是一个数据仓库基础工具在Hadoop中用来处理结构化数据。
http://www.yiibai.com/hive/
http://172.31.50.110:80/YumLearning/index.html
  
  进入hive query的界面，便可执行一些sql  
  注意：
Hive 没有索引，存储过程，outer join，
也不能delete 和 update 
## Hive 表的几种类型
* 内部表 
* 外部表 
* 分区表 
* 桶表   

其中 内部表和分区表用的最多，外部表偶尔用（且多是临时表），桶表（使用hash分区）几乎不用 
所以着重介绍内部表和分区的用法 
ps: – 为避免不必要的错误，对表做任何操作时，最后都带上他所属的database 
   – 格式是 xxx_database.xxx_table  
 * 内部表和外部表的区别：  
内部表是将数据存在hive自己的warehouse中，drop表 数据也会被删掉
而外部表更像是将表与数据之间建立了一个指针，数据存放在hdfs的任何目录下，不会被强制迁移到hive的目录下， 所以即使表被删除，数据仍然存在原来的目录下。
外部表的效率会比内部表低
* 建表：  
```sql
-- 建一张普通的内部表
    create table daliy_analysis.test_create_new_table 
    (userid int,
     username string,)
-- 从别的表中抽取字段：
    create table daliy_analysis.test_select_new_table as
    select column1,column2 from table2 
    where column3!=null
-- 创建一张表结构和另一张表一毛一样的表：
    create table daliy_analysis.test_copy_table like xxx_table;
-- 将自己上传到hdfs的文件数据存入表
   -- 先建立好表，并指明分隔符和存储方式
    create table daliy_analysis.test_create_new_table
    (userid int,
     username string,)
```
