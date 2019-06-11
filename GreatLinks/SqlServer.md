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


# 函数
#CONCAT() 类似于string.format() 将数据进行拼接起来
select name,CONCAT(url,',',alexa,',',country)as info from Websites as site