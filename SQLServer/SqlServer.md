
@基本知识
# 约束
UNIQUE - 保证某列的每行数据不重复

PRIMARY KEY - NOT NULL 和 UNIQUE 的结合。确保某列（或两个列多个列的结合）有唯一标识，有助于更容易更快速地找到表中的一个特定的记录。
#类似于学生表的学号，或者课程表的课程编号

FOREIGN KEY - 保证一个表中的数据匹配另一个表中的值的参照完整性。
#类似于成绩表的学号或者课程编号

CHECK - 保证列中的值符合指定的条件。


@表的增删改查
#1 Create new Tebale(Websites) Id is Identity
CREATE TABLE Websites
(
	[Id] INT NOT NULL PRIMARY KEY, 
    [name] NCHAR(20) NULL, 
    [url] NCHAR(30) NULL, 
    [alexa] INT NULL, 
    [country] CHAR(10) NULL
)

CREATE TABLE access_log
(
	[aid] INT NOT NULL PRIMARY KEY, 
    [site_id] int NULL, 
    [count] int NULL, 
    [date] datetime NULL
)
Create table apps
(
	[id] INT NOT NULL PRIMARY KEY,
	[app_name] nchar(20) null,
	[url] nchar(30) null,
	[country] char(10) null
)

#2 Insert Values 
#2.1 specific coumn name
insert into [dbo].[Websites] (name,url,alexa,country) values ('Google','https://www.google.com',1,'USA')
#2.2 not specific
insert into [dbo].[Websites] values ('淘宝','https://www.taobao.com',13,'CN')
#2.3 Multi-line data
insert into [dbo].[Websites] values ('菜鸟教程','https://www.runoob.com',4689,'CN'),('微博','https://www.weibo.com',20,'CN'),('Facebook','https://www.facebook.com',13,'USA'

# insert into access_log 注意日期必须添加引号，不然会按照数字插入
insert into access_log (site_id,count,date) values(1,45,'2016-05-10'),(3,100,'2016-05-13'),(1,230,'2016-05-14')
,(2,10,'2016-05-14'),(5,205,'2016-05-14'),(4,13,'2016-05-15'),(3,220,'2016-05-15'),(5,545,'2016-05-16'),(3,201,'2016-05-17')

#apps
insert into apps values('QQ APP','http://in.qq.com','CN'),
('weibo APP','http://weibo.com','CN'),('taobao APP','https://www.taobao.com','CN')

#3. select 
#3.0 select distinct 
select distinct country from Websites
#select where 
select url from Websites where name ='Google'


#3.1 where like
select url from Websites where name like 'Goo%'
#3.1.2 select where not like 
select top 2 * from Websites where name not like 'Goo%' 


#3.2 where in
select url from Websites where name in ('Google','taobao')
#3.2 where and\or
select url from Websites where name in ('Google','taobao') and alexa>5


#3.3 between 
select top 2 * from Websites where alexa between 1 and 20
#匹配名字首字母在'A'到'H'之间
select * from Websites where name between 'A' and 'H'

#3.3.2 not between
select * from Websites where alexa not between 1 and 20



#3-2 select top
#3.2.1 select top top排在order后面 所以会先倒序 再取值
select top 5 * from Websites order by alexa desc
# 如果需要实现 
with c as (select top 5 * from Websites) 
select * from c join Websites as b on c.Id=b.Id order by c.alexa 
#3.2.2 select top percent 
select top 50 percent * from Websites



#4 Order By 
select name,url from Websites order by alexa Desc
#4.1 a desc b asc
select name,url from Websites order by alexa desc, country asc

#5 Update 
#5.1 update 不加where语句所有行都会被更改 (sql_safe_updates 这个自带的参数来解决，当该参数开启的情况下，你必须在update 语句后携带 where 条件，否则就会报错。)
update Websites set alexa =5001, country='USA' where name='cainiao'

#6 Delete
#6.1 delete a row 不添加where会删除所有行但不改变表结构
delete from Websites where id =6 and name='baidu'

# 注意 删除表之后自增的id不会从1开始 如果需要设置
truncate table access_log 

#7 别名 可以将列名或者查到的表名指定为更有意义的名字
select name as n, country as c from Websites
select name,country from Websites as site

#表的连接
#8 Join 
#8.1 inner join 等值连接 返回两个表中连接字段相等的行
SELECT Websites.name, access_log.count, access_log.date
FROM Websites
INNER JOIN access_log
ON Websites.id=access_log.site_id

#8.2 left Join  左连接，返回左表中所有的记录以及右表中连接字段相等的记录。
select w.name,a.count,a.date 
from Websites w inner join access_log a 
on w.Id=a.site_id 
order by a.count

#8.2.1在使用 left jion 时，on 和 where 条件的区别如下：
#1、 on 条件是在生成临时表时使用的条件，它不管 on 中的条件是否为真，都会返回左边表中的记录。
#2、where 条件是在临时表生成好后，再对临时表进行过滤的条件。这时已经没有 left join 的含义（必须返回左边表的记录）了，条件不为真的就全部过滤掉。

#8.3 right join : 右连接，返回右表中所有的记录以及左表中连接字段相等的记录。

#8.4 full join : 外连接，返回两个表中的行：left join + right join。

#表的合并
#9 UNION 操作符用于合并两个或多个 SELECT 语句的结果集。
#请注意，UNION 内部的每个 SELECT 语句必须拥有相同数量的列。列也必须拥有相似的数据类型。同时，每个 SELECT 语句中的列的顺序必须相同。
# 类似合并同类项，但是位置不能反
select name,country from Websites union select app_name, country from apps order by country

#9.1 UNION 是不允许重复的，如果允许重复，就要使用UNIION ALL
SELECT name,country from Websites
UNION ALL
SELECT app_name,country from apps
#9.1.2 但如果需要使用where子句,就必须将每个子句添加where检索
SELECT name,country from Websites
WHERE country='CN'
UNION ALL
SELECT app_name,country from apps
WHERE country='CN'

#表的复制

#表的备份
#10 SELECT INTO  语句从一个表复制数据，然后把数据插入到另一个新表中。
#可以从当前表中复制任意数据到一个空的(无结构，多为不存在的)表中
select id into newApps from apps

#10.2 从多个表中复制，但是这样会产生 count(Id)*count(app_name)行数据
select Websites.Id,apps.app_name into newTest from apps,Websites

#10.3 当然我们也可以创建一个空的新表（只复制结构），只需要添加促使查询没有数据返回的 WHERE 子句即可：
SELECT *
INTO newtable
FROM table1
WHERE 1=0;

#复制并插入
# 10.4 INSERT INTO SELECT 语句从一个表复制数据，然后把数据插入到一个已存在的表中。
#目标表中任何已存在的行都不会受影响。

#如果两个表结构一样：
insert into table_name_new select * from table_name_old

#如果两个表结构不一样：这种会把数据添加到最下面，没有数据的自动为空

insert into table_name_new(column1,column2...) select column1,column2... from table_name_old





# 函数
#CONCAT() 类似于string.format() 将数据进行拼接起来
select name,CONCAT(url,',',alexa,',',country)as info from Websites as site