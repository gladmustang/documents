SQLServer中用T—SQL命令查询一个数据库中有哪些表的sql语句

作者： 字体：[增加 减小] 类型：转载 时间：2012-06-27 我要评论

SQLServer如何用T—SQL命令查询一个数据库中有哪些表，方便进行表操作，需要的朋友可以参考下

  查看帮助： sp_help;

1、查询SQL中的所有表： 

Select TABLE_NAME FROM 数据库名称.INFORMATION_SCHEMA.TABLES Where TABLE_TYPE='BASE TABLE' 执行之后，就可以看到数据库中所有属于自己建的表的名称 

2、查询SQL中所有表及列： 

Select dbo.sysobjects.name as Table_name, dbo.syscolumns.name AS Column_name FROM dbo.syscolumns INNER JOIN dbo.sysobjects ON dbo.syscolumns.id = dbo.sysobjects.id Where (dbo.sysobjects.xtype = 'u') AND (NOT (dbo.sysobjects.name LIKE 'dtproperties')) 

3、在Sql查询分析器，还有一个简单的查询方法： 

EXEC sp_MSforeachtable @command1="sp_spaceused '?'" 执行完之后，就可以看到数据库中所有用户表的信息 

4、查询总存储过程数: 

select count(*) 总存储过程数 from sysobjects where xtype='p' 

D = 默认值或 DEFAULT 约束 

F = FOREIGN KEY 约束 

L = 日志 

FN = 标量函数 

IF = 内嵌表函数 

P = 存储过程 

PK = PRIMARY KEY 约束（类型是 K） 

RF = 复制筛选存储过程 

S = 系统表 

TF = 表函数 

TR = 触发器 

U = 用户表 

UQ = UNIQUE 约束（类型是 K） 

V = 视图 

X = 扩展存储过程