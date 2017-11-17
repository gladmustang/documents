IF EXISTS (select * from information_schema.schemata where schema_name='dbo')

        IF EXISTS (select * from information_schema.tables where table_schema='dbo' and table_name='test')

                select * from test;

GO

CREATE TABLE tt(ll varchar(22) PRIMARY KEY, value text);

-- up:

select * from testSchema.migrat

drop table testSchema.migrat

select * from test

ALTER TABLE test ADD address varchar(30);

  Alter table [HFFS_JHH_Rev].[dbo].transactions alter column pwc_transaction_id int not null

alter table [HFFS_JHH_Rev].[dbo].transactions add constraint pk_trans primary key (pwc_transaction_id)

Sql Server Alter语句

在修改Sql Server表结构时，常用到Alter语句，把一些常用的alter语句列举如下。

1：向表中添加字段

Alter table [表名] add [列名] 类型

2: 删除字段

Alter table [表名] drop column [列名]

3: 修改表中字段类型 （可以修改列的类型，是否为空）

Alter table [表名] alter column [列名] 类型

4：添加主键

Alter table [表名] add constraint [ 约束名] primary key( [列名])

          Example: alter table halo.PwC_Claims_100M_2 add constraint pk_id primary key(id)

5：添加唯一约束

Alter table [表名] add constraint [ 约束名] unique([列名])

6：添加表中某列的默认值

Alter table [表名] add constraint [约束名] default(默认值) for [列名]

7：添加约束

Alter table [表名] add constraint [约束名] check (内容)

8:添加外键约束

 Alter table [表名] add constraint [约束名] foreign key(列名) referencese 另一表名(列名)

9:删除约束

Alter table [表名] drop constraint [约束名] 

10:重命名表

exec sp_rename '[原表名]','[新表名]'

11：重命名列名

exec sp_rename '[表名].[列名]','[表名].[新列名]'

创建注释（N'user', N'dbo', N'TABLE' 为固定的写法）

12：为表添加描述信息

EXECUTE sp_addextendedproperty N'MS_Description', '人员信息表', N'user', N'dbo', N'TABLE', N'表名', NULL, NULL

13：为字段Username添加描述信息

EXECUTE sp_addextendedproperty N'MS_Description', '姓名', N'user', N'dbo', N'TABLE', N'表名', N'column', N'Username'

14：为字段Sex添加描述信息

EXECUTE sp_addextendedproperty N'MS_Description', '性别', N'user', N'dbo', N'TABLE', N'表名', N'column', N'Sex'

15：更新表中列UserName的描述属性：

EXEC sp_updateextendedproperty 'MS_Description','新的姓名','user',dbo,'TABLE','表名','column','UserName'

16：删除表中列UserName的描述属性：

EXEC sp_dropextendedproperty 'MS_Description','user',dbo,'TABLE','表名','column','Username'

insert into [HFFS_JHH_Rev].[pbc_tb].[hffs_attributes] (

      [Attribute_name]

      ,[is_cdm]

      ,[Data_type]

      ,[size]

      ,[default_value]

      ,[ins_date]

      ,[ins_by]

      ,[updated_date]

      ,[updated_by]

      ,[plan_type]

      ,[is_required])

          values ('FSLI', 'N', null, 255, null, getDate(), 'Todd', null, null, 'Trial Balance', 'Y')