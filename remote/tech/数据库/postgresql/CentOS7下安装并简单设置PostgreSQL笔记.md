[<span style="color: rgb(86,182,233);font-size: 13px;font-family: Verdana, Arial, helvetica, sans-seriff;">CentOS7下安装并简单设置PostgreSQL笔记</span>](http://www.cnblogs.com/think8848/p/5877076.html)

# <span style="color: rgb(35,35,35);font-size: 28px;font-family: Verdana, Arial, helvetica, sans-seriff;">为什么是PostgreSQL?</span>

<span style="color: rgb(35,35,35);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;">在.NET Core诞生之前，微软平台上最常见的开发组件便是.NET Framework + SQL Server了，但是现在.NET Core终于让跨平台部署成为了现实，这一模式还会常见吗？个人认为这一黄金搭档很可能会日渐势微了，因为未来很多的.NET应用将部署在Linux上，为了使用SQL Server，人们又部署一个Windows环境吗？想想都觉得不大可能，那么为Linux上的.NET Core选择一款合适的数据库就变得非常重要。其实也不难选，因为就两个选项，一个是MySQL(The world’s most popular open-source database),另一个是PostgreSQL(The world's most advanced open source database)，从目前我的认知而言，我选择了PostgreSQL。</span>

<span style="color: rgb(35,35,35);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;">在51job上全文搜索MySQL,有1568页内容，而全文搜索PostgreSQL则只有44页内容(2016年9月16日数据)，这说明使用MySQL的企业和从业人员数据远超PostgreSQL数据，那为什么我还要选择PostgreSQL呢？这要从三个方面谈起，一是我曾学习并使用过MySQL，感觉MySQL上手容易，精通困难，一般程序员没有经过培训驾驭不了MySQL，当时有个项目，开发阶段貌似和SQL Server区别不大，但是系统部署到生产环境之后很快性能问题就会暴露出来了，为此我不得不赶鸭子上架，边学边用，重构了整个数据访问层,(有同学可能会问了，PostgreSQL可能比MySQL还要难上手，额，我最担心的是项目组中有人SQL脚本技术不过关，MySQL对于脚本的优化做的又不咋滴...)；第二是我目前对GIS应用系统比较感兴趣，而PostgreSQL有一个MySQL无法比拟的优势，那就是PostGIS，PostGIS可以完美支持空间数据存储和空间分析；三是从PostgreSQL9.3起就内置了JSON数据类型，而9.4又开始支持JSONB，这标志着PostgreSQL实际上已经是一个关系型数据库和NoSQL数据库的结合体了，而且有</span>[<span style="color: rgb(86,182,233);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;">消息</span>](http://www.infoq.com/cn/news/2014/09/postgres-outperforms-mongodb/)<span style="color: rgb(35,35,35);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;">表明，PostgreSQL的NoSQL性能有益到甚至超过了MongoDB！，这对于GIS大数据应用是多么好的一个消息啊。我还有什么理由拒绝PostgreSQL呢？</span>

<span style="color: rgb(35,35,35);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;">~~~~~~~~~~~~~~~~我是分割线，以上都是废话~~~~~~~~~~~~~~~~</span>

<span style="color: rgb(35,35,35);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;">安装环境：CentOS7.2，与</span>[<span style="color: rgb(86,182,233);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;">此处</span>](http://www.cnblogs.com/think8848/p/5862469.html)<span style="color: rgb(35,35,35);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;">环境相同</span>

<span style="color: rgb(35,35,35);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;">在安装之前，先看看官方的</span>[<span style="color: rgb(86,182,233);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;">安装说明</span>](https://www.postgresql.org/download/linux/redhat/)<span style="color: rgb(35,35,35);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;">总是一个好习惯</span>

<span style="color: rgb(35,35,35);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;">CentOS7.2中自带的PostgreSQL是9.2版本的，里面没有NoSQL特性，因此我们使用rpm包安装方式，PostgreSQL的repository包地址列表在</span>[<span style="color: rgb(86,182,233);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;">这里</span>](http://yum.postgresql.org/repopackages.php)<span style="color: rgb(35,35,35);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;">。</span>

<span style="color: rgb(35,35,35);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;">1\. 首先安装PostgreSQL的rpm</span>

<pre><span style="color: rgb(0,0,0);background-color: rgb(245,245,245);font-size: 12px;">sudo yum install http://yum.postgresql.org/9.5/redhat/rhel-7-x86_64/pgdg-redhat95-9.5-2.noarch.rpm -y</span></pre>

<span style="color: rgb(35,35,35);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;">2\. 然后再安装PostgreSQL服务器和第三方扩展包</span>

<pre><span style="color: rgb(0,0,0);background-color: rgb(245,245,245);font-size: 12px;">sudo yum install postgresql95-server postgresql95-contrib -y</span></pre>

<span style="color: rgb(35,35,35);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;">3\. 初始化数据库(请看下面更新部分)</span>

<pre><span style="color: rgb(0,0,0);background-color: rgb(245,245,245);font-size: 12px;">sudo /usr/pgsql-9.5/bin/postgresql95-setup initdb</span></pre>

<span style="color: rgb(35,35,35);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;">---------------------------</span><span style="color: rgb(255,0,0);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;">我是分割线，2016.10.26更新开始</span><span style="color: rgb(35,35,35);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;">---------------------------</span>

<span style="color: rgb(35,35,35);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;">3\. 默认情况下，Postgresql安装目录是/usr/pgsql-9.5,而Postgresql的数据目录是/var/lib/pgsql/版本号/data目录，如果你从一开始就规划了/var很大磁盘空间，就没有问题，但是一旦你的/var目录空间并不大，那么就要考虑在安装Postgresql时指定安装目录了，在本例中，我们假定/home的空间很大。</span>

<span style="color: rgb(35,35,35);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;">首先在/home下创建一个Postgresql的数据目录</span>

<pre><span style="color: rgb(0,0,0);background-color: rgb(245,245,245);font-size: 12px;">sudo mkdir /home/postgresql_data</span></pre>

<span style="color: rgb(35,35,35);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;">然后为这个目录指定所有者同时分配权限</span>

<pre><span style="color: rgb(0,0,0);background-color: rgb(245,245,245);font-size: 12px;">sudo chown postgres:postgres /home/postgresql_data</span>  

<span style="color: rgb(0,0,0);background-color: rgb(245,245,245);font-size: 12px;">sudo chmod 750 /home/postgresql_data</span></pre>

<span style="color: rgb(35,35,35);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;">然后设置环境变量</span>

<pre><span style="color: rgb(0,0,0);background-color: rgb(245,245,245);font-size: 12px;">export PATH=/usr/pgsql-9.5/bin:</span><span style="color: rgb(128,0,128);background-color: rgb(245,245,245);font-size: 12px;">$PATH</span>  

<span style="color: rgb(0,0,0);background-color: rgb(245,245,245);font-size: 12px;">export LD_LIBRARY_PATH=/usr/pgsql-9.5/lib</span>  

<span style="color: rgb(0,0,0);background-color: rgb(245,245,245);font-size: 12px;">export PGDATA=/home/postgresql_data</span></pre>

<span style="color: rgb(35,35,35);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;">然后使用命令initdb生成数据库簇,在此之此，请切换至postgres用户</span>

<pre><span style="color: rgb(0,0,0);background-color: rgb(245,245,245);font-size: 12px;">initdb</span></pre>

<span style="color: rgb(35,35,35);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;">最后尝试启动Postgresql服务</span>

<pre><span style="color: rgb(0,0,0);background-color: rgb(245,245,245);font-size: 12px;">pg_ctl start -D</span> <span style="color: rgb(128,0,128);background-color: rgb(245,245,245);font-size: 12px;">$PGDATA</span></pre>

<span style="color: rgb(35,35,35);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;">使用 </span><span style="color: rgb(0,0,0);background-color: rgb(245,245,245);font-size: 12px;">ps -ef | grep postgres</span><span style="color: rgb(35,35,35);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;"> 验证，如果有一堆postgres相关进程，那就安装成功了。</span>

<span style="color: rgb(35,35,35);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;">如果就到此结束了，貌似第4步就没法做了，因为使用 </span><span style="color: rgb(0,0,0);background-color: rgb(245,245,245);font-size: 12px;">systemctl start postgresql-9.5</span><span style="color: rgb(35,35,35);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;"> 将不会成功的，为啥呢？请打开 </span><span style="color: rgb(0,0,0);background-color: rgb(245,245,245);font-size: 12px;">sudo vi /usr/lib/systemd/system/postgresql-9.5.service</span><span style="color: rgb(35,35,35);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;"> ，因为在#Location of database direcotry配置节里面没有指定正确的PGDATA。所以我们需要将下面的PGDATA设置成正确值</span>

<pre><span style="color: rgb(0,128,0);background-color: rgb(245,245,245);font-size: 12px;">#Location of database directory</span>  
<span style="color: rgb(0,0,0);background-color: rgb(245,245,245);font-size: 12px;">Environment=PGDATA=/home/postgresql_data</span></pre>

<span style="color: rgb(35,35,35);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;">---------------------------</span><span style="color: rgb(255,0,0);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;">我是分割线，2016.10.26更新结束</span><span style="color: rgb(35,35,35);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;">---------------------------</span>

<span style="color: rgb(35,35,35);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;">4\. 配置数据库服务开机启动并立即启动数据库服务</span>

<pre><span style="color: rgb(0,0,0);background-color: rgb(245,245,245);font-size: 12px;">sudo systemctl enable postgresql-9.5.service</span>  

<span style="color: rgb(0,0,0);background-color: rgb(245,245,245);font-size: 12px;">sudo service postgresql-9.5 start</span></pre>

<span style="color: rgb(35,35,35);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;">5\. 检查数据库服务状态，有绿色，没红色说明启动OK了</span>

<pre><span style="color: rgb(0,0,0);background-color: rgb(245,245,245);font-size: 12px;">service postgresql-9.5 status</span></pre>

![](http://images2015.cnblogs.com/blog/1781/201609/1781-20160916205819555-1948320262.png)

<span style="color: rgb(35,35,35);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;">6\. 修改postgres用户密码，切换到postgres用户</span>

<pre><span style="color: rgb(0,0,0);background-color: rgb(245,245,245);font-size: 12px;">sudo passwd postgres</span>  

<span style="color: rgb(0,0,0);background-color: rgb(245,245,245);font-size: 12px;">su postgres</span></pre>

![](http://images2015.cnblogs.com/blog/1781/201609/1781-20160916210642148-1058446611.png)

<span style="color: rgb(35,35,35);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;">7\. 然后使用psql工具登录数据库，列出当前的数据库，命令分别是 </span><span style="color: rgb(0,0,0);background-color: rgb(245,245,245);font-size: 12px;">psql</span><span style="color: rgb(35,35,35);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;"> 和 </span><span style="color: rgb(0,0,0);background-color: rgb(245,245,245);font-size: 12px;">\l</span> 

![](http://images2015.cnblogs.com/blog/1781/201609/1781-20160916210804742-1736807003.png)

<span style="color: rgb(35,35,35);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;">**在CentOS上，默认的PostgreSQL数据目录是/var/lib/pgsql/版本号/data**</span>

<span style="color: rgb(35,35,35);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;">PostgreSQL的配置文件就在这个目录下/var/lib/pgsql/版本号/data/postgresql.conf,还有一个配置文件也需要稍加关注，那就是访问控制配置文件/var/lib/pgsql/版本号/data/pg_hba.conf</span>

<span style="color: rgb(35,35,35);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;">8\. 下面需要先对服务配置文件postgresql.conf进行一些设置：</span>

<span style="color: rgb(35,35,35);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;">将 </span><span style="color: rgb(0,0,0);background-color: rgb(245,245,245);font-size: 12px;">#listen_addresses = 'localhost'</span><span style="color: rgb(35,35,35);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;"> 前的#号去掉，然后将后面的localhost改为*，然后将 </span><span style="color: rgb(0,128,0);background-color: rgb(245,245,245);font-size: 12px;">#port = 5432</span><span style="color: rgb(35,35,35);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;"> 前的#去掉,最后再将 </span><span style="color: rgb(0,128,0);background-color: rgb(245,245,245);font-size: 12px;">#password_encryption = on</span><span style="color: rgb(35,35,35);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;"> 前面的#号去掉，如下图所示，使用wq命令保存退出。</span>

![](http://images2015.cnblogs.com/blog/1781/201609/1781-20160916234627367-112430444.png)

<span style="color: rgb(35,35,35);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;">(友情提示：postgresql.conf中可以修改的参数很多，上图中第2个红框可以修改侦听端口，另外此文件内还可以修改缓存大小等多种参数)</span>

<span style="color: rgb(35,35,35);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;">9\. 再对pg_hba.conf内容进行配置，将上面红框内的ident改为md5,然后再在最下面加入 </span><span style="color: rgb(0,0,0);background-color: rgb(245,245,245);font-size: 12px;">host all all 0.0.0.0/0 md5</span><span style="color: rgb(35,35,35);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;"> ，如下图所示：</span>

![](http://images2015.cnblogs.com/blog/1781/201609/1781-20160916235105711-1513724966.png)

<span style="color: rgb(35,35,35);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;">10\. 重启postgresql-9.5服务，使配置文件重效</span>

<pre><span style="color: rgb(0,0,0);background-color: rgb(245,245,245);font-size: 12px;">service postgresql-9.5 restart</span></pre>

<span style="color: rgb(35,35,35);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;">11\. 接下来我们创建一个数据库</span>

<pre><span style="color: rgb(0,0,0);background-color: rgb(245,245,245);font-size: 12px;">psql</span></pre>

<pre><span style="color: rgb(0,0,255);background-color: rgb(245,245,245);font-size: 12px;">CREATE</span> <span style="color: rgb(0,0,255);background-color: rgb(245,245,245);font-size: 12px;">DATABASE</span> <span style="color: rgb(0,0,0);background-color: rgb(245,245,245);font-size: 12px;">testdb;</span></pre>

<span style="color: rgb(35,35,35);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;">如下图所示，我们就创建了一个名为testdb的数据库，</span>

![](http://images2015.cnblogs.com/blog/1781/201609/1781-20160916235640602-436004747.png)

<span style="color: rgb(35,35,35);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;">12.然后再创建一名用户</span>

<pre><span style="color: rgb(0,0,0);background-color: rgb(245,245,245);font-size: 12px;font-family: Verdana, Arial, helvetica, sans-seriff;">CREATE</span> <span style="color: rgb(0,0,0);background-color: rgb(245,245,245);font-size: 12px;font-family: Verdana, Arial, helvetica, sans-seriff;">USER think8848 CREATEDB LOGIN PASSWORD '111111'</span></pre>

<span style="color: rgb(35,35,35);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;">如下图所示，这样我们就创建了一个名为think8848的用户，后面的 </span><span style="color: rgb(0,0,0);background-color: rgb(245,245,245);font-size: 12px;">CREATEDB LOGIN PASSWORD</span> <span style="color: rgb(255,0,0);background-color: rgb(245,245,245);font-size: 12px;">'111111'</span><span style="color: rgb(35,35,35);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;"> 意思是这个用户可以创建数据库，还可以登录，他的密码是111111</span>

![](http://images2015.cnblogs.com/blog/1781/201609/1781-20160917000020805-406001744.png)

<span style="color: rgb(35,35,35);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;">13\. 接下来将testdb的所有权限都分配给think8848同学</span>

<pre><span style="color: rgb(0,0,0);background-color: rgb(245,245,245);font-size: 14px;">GRANT</span> <span style="color: rgb(0,0,0);background-color: rgb(245,245,245);font-size: 14px;">ALL</span> <span style="color: rgb(0,0,0);background-color: rgb(245,245,245);font-size: 14px;">ON</span> <span style="color: rgb(0,0,0);background-color: rgb(245,245,245);font-size: 14px;">DATABASE testdb TO think8848</span></pre>

![](http://images2015.cnblogs.com/blog/1781/201609/1781-20160917000425555-1143614894.png)

<span style="color: rgb(35,35,35);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;">14\. 退出postgres用户登录，命令为**\q**, 对，你没看错，就是一个反斜杠和一个q</span>

<span style="color: rgb(35,35,35);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;">15. 开启防火墙5432端口</span>

<pre><span style="color: rgb(0,0,0);background-color: rgb(245,245,245);font-size: 12px;">sudo firewall-cmd --zone=public --add-port=5432/tcp --permanent</span>  

<span style="color: rgb(0,0,0);background-color: rgb(245,245,245);font-size: 12px;">sudo firewall-cmd --reload</span></pre>

<span style="color: rgb(35,35,35);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;">16\. 尝试用think8848登录数据库</span>

<pre><span style="color: rgb(0,0,0);background-color: rgb(245,245,245);font-size: 12px;">psql -U think8848 -h 127.0.0.1 -p 5432 -d testdb -W</span></pre>

![](http://images2015.cnblogs.com/blog/1781/201609/1781-20160917001005586-651401338.png)

<span style="color: rgb(35,35,35);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;">**最后，再说两个psql很常用的命令，一个\c,切换数据库，如: **</span><span style="color: rgb(0,0,0);background-color: rgb(245,245,245);font-size: 12px;">\c postgres;** ,它的作用和SQL Server的 **use postgres;** 一样；另一个是\d，此命令是列出当前库下所有的表。**</span>

![](http://images2015.cnblogs.com/blog/1781/201609/1781-20160917003450695-1763410743.png)

<span style="color: rgb(35,35,35);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;">17\. 我打算使用PostgreSQL做数据库服务器，但是从没打算使用psql当管理工具，所以还是要找个GUI的管理工具才行啊，也不知道哪个好，先随手抓过来一个用用看，pgAdmin4,下载地址在</span>[<span style="color: rgb(86,182,233);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;">这里</span>](https://www.pgadmin.org/download/windows4.php)<span style="color: rgb(35,35,35);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;"> ,</span>

<span style="color: rgb(35,35,35);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;">先建个Server看看都有什么</span>

![](http://images2015.cnblogs.com/blog/1781/201609/1781-20160917001500383-1864466095.png)

<span style="color: rgb(35,35,35);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;">再给起个响亮点的名称</span>

![](http://images2015.cnblogs.com/blog/1781/201609/1781-20160917001616836-948055576.png)

<span style="color: rgb(35,35,35);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;">然后再配置服务器IP等信息</span>

![](http://images2015.cnblogs.com/blog/1781/201609/1781-20160917001852539-833220905.png)

<span style="color: rgb(35,35,35);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;">点了Save后并没有什么反应，在Servers上点击右键Refresh，还是没有什么效果,难道这货没有用？好吧，再试试IT人员的杀手级技巧吧，关了程序重新打开，这时...</span>

![](http://images2015.cnblogs.com/blog/1781/201609/1781-20160917002126680-2135457893.png)

<span style="color: rgb(35,35,35);font-size: 14px;font-family: Verdana, Arial, helvetica, sans-seriff;">看起来还不错，可以用图形化界面管理数据库，然后又是免费的，我们不能要求太多，对吧？</span>