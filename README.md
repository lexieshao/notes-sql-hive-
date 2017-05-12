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
