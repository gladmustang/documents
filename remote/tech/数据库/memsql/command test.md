<span style="color: rgb(0,136,187);background-color: rgb(242,242,242);">`LOAD DATA INFILE '/root/memsql/1.tsv'INTO TABLE foo ;`</span>

<span style="color: rgb(0,136,187);background-color: rgb(242,242,242);">`每次load是添加进新的记录，不是覆盖。`</span>

<span style="color: rgb(0,136,187);background-color: rgb(242,242,242);">`1\. create table`</span>

<span style="color: rgb(0,136,187);background-color: rgb(242,242,242);">`create table foo2 (id int AUTO_INCREMENT key, name varchar(255), value varchar(255));`</span>

<span style="color: rgb(0,136,187);background-color: rgb(242,242,242);">`2\. load data`</span>

<span style="color: rgb(0,136,187);background-color: rgb(242,242,242);">`LOAD DATA INFILE '/root/memsql/1.tsv'INTO TABLE foo2 (name, value) ;`</span>

<span style="color: rgb(0,136,187);background-color: rgb(242,242,242);">`3\.`</span>

<span style="color: rgb(0,136,187);background-color: rgb(242,242,242);">`CREATE OR REPLACE PROCEDURE tt() AS`</span>

<span style="color: rgb(0,136,187);background-color: rgb(242,242,242);">`BEGIN`</span>

<span style="color: rgb(0,136,187);background-color: rgb(242,242,242);">`END;`</span>

<span style="color: rgb(0,136,187);background-color: rgb(242,242,242);">`delimiter //`</span>

<span style="color: rgb(0,136,187);background-color: rgb(241,241,241);font-size: 14px;font-family: monospace;">CREATE OR REPLACE PROCEDURE tt() AS</span>

<span style="color: rgb(0,136,187);background-color: rgb(241,241,241);font-size: 14px;font-family: monospace;">declare a int =1;</span>

<span style="color: rgb(0,136,187);background-color: rgb(241,241,241);font-size: 14px;font-family: monospace;">BEGIN</span>

<span style="color: rgb(0,136,187);background-color: rgb(241,241,241);font-size: 14px;font-family: monospace;">END; //</span>

<span style="color: rgb(0,136,187);background-color: rgb(241,241,241);font-size: 14px;font-family: monospace;">delimiter ;</span>

<span style="color: rgb(0,136,187);background-color: rgb(242,242,242);">`4.`</span>

<span style="color: rgb(0,136,187);background-color: rgb(242,242,242);">`show create procedure tt;`</span>