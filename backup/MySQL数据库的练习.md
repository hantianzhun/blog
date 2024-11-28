### 1.导入exam-utf8（无外键）数据库

> [!TIP]
> 导入数据库是为了方便后面的查询练习

```sql
DROP database IF EXISTS exam;

CREATE DATABASE IF NOT EXISTS exam CHARSET=utf8;  

USE exam;

/*创建部门表*/
CREATE TABLE dept(
deptno INT PRIMARY KEY,
dname VARCHAR(50),
loc VARCHAR(50)
);

/*创建雇员表*/
CREATE TABLE emp(
empno INT PRIMARY KEY,
ename VARCHAR(50),
job VARCHAR(50),
mgr INT,
hiredate DATE,
sal DECIMAL(7,2),
COMM DECIMAL(7,2),
deptno INT
);

/*创建工资等级表*/
CREATE TABLE salgrade(
grade INT PRIMARY KEY,
losal INT,
hisal INT
);

/*创建学生表*/
CREATE TABLE stu(
sid INT PRIMARY KEY,
sname VARCHAR(50),
age INT,
gander VARCHAR(10),
province VARCHAR(50),
tuition INT
);

/*插入dept表数据*/
INSERT INTO dept VALUES (10, '教研部', '北京');
INSERT INTO dept VALUES (20, '学工部', '上海');
INSERT INTO dept VALUES (30, '销售部', '广州');
INSERT INTO dept VALUES (40, '财务部', '武汉');

/*插入emp表数据*/
INSERT INTO emp VALUES (1009, '曾阿牛', '董事长', NULL, '2001-11-17', 50000, NULL, 10);
INSERT INTO emp VALUES (1004, '刘备', '经理', 1009, '2001-04-02', 29750, NULL, 20);
INSERT INTO emp VALUES (1006, '关羽', '经理', 1009, '2001-05-01', 28500, NULL, 30);
INSERT INTO emp VALUES (1007, '张飞', '经理', 1009, '2001-09-01', 24500, NULL, 10);
INSERT INTO emp VALUES (1008, '诸葛亮', '分析师', 1004, '2007-04-19', 30000, NULL, 20);
INSERT INTO emp VALUES (1013, '庞统', '分析师', 1004, '2001-12-03', 30000, NULL, 20);
INSERT INTO emp VALUES (1002, '黛绮丝', '销售员', 1006, '2001-02-20', 16000, 3000, 30);
INSERT INTO emp VALUES (1003, '殷天正', '销售员', 1006, '2001-02-22', 12500, 5000, 30);
INSERT INTO emp VALUES (1005, '谢逊', '销售员', 1006, '2001-09-28', 12500, 14000, 30);
INSERT INTO emp VALUES (1010, '韦一笑', '销售员', 1006, '2001-09-08', 15000, 0, 30);
INSERT INTO emp VALUES (1012, '程普', '文员', 1006, '2001-12-03', 9500, NULL, 30);
INSERT INTO emp VALUES (1014, '黄盖', '文员', 1007, '2002-01-23', 13000, NULL, 10);
INSERT INTO emp VALUES (1011, '周泰', '文员', 1008, '2007-05-23', 11000, NULL, 20);


INSERT INTO emp VALUES (1001, '甘宁', '文员', 1013, '2000-12-17', 8000, NULL, 20);

/*插入salgrade表数据*/
INSERT INTO salgrade VALUES (1, 7000, 12000);
INSERT INTO salgrade VALUES (2, 12010, 14000);
INSERT INTO salgrade VALUES (3, 14010, 20000);
INSERT INTO salgrade VALUES (4, 20010, 30000);
INSERT INTO salgrade VALUES (5, 30010, 99990);

/*插入stu表数据*/
INSERT INTO `stu` VALUES ('1', '王永', '23', '男', '北京', '1500');
INSERT INTO `stu` VALUES ('2', '张雷', '25', '男', '辽宁', '2500');
INSERT INTO `stu` VALUES ('3', '李强', '22', '男', '北京', '3500');
INSERT INTO `stu` VALUES ('4', '宋永合', '25', '男', '北京', '1500');
INSERT INTO `stu` VALUES ('5', '叙美丽', '23', '女', '北京', '1000');
INSERT INTO `stu` VALUES ('6', '陈宁', '22', '女', '山东', '2500');
INSERT INTO `stu` VALUES ('7', '王丽', '21', '女', '北京', '1600');
INSERT INTO `stu` VALUES ('8', '李永', '23', '男', '北京', '3500');
INSERT INTO `stu` VALUES ('9', '张玲', '23', '女', '广州', '2500');
INSERT INTO `stu` VALUES ('10', '啊历', '18', '男', '山西', '3500');
INSERT INTO `stu` VALUES ('11', '王刚', '23', '男', '湖北', '4500');
INSERT INTO `stu` VALUES ('12', '陈永', '24', '男', '北京', '1500');
INSERT INTO `stu` VALUES ('13', '李雷', '24', '男', '辽宁', '2500');
INSERT INTO `stu` VALUES ('14', '李沿', '22', '男', '北京', '3500');
INSERT INTO `stu` VALUES ('15', '王小明', '25', '男', '北京', '1500');
INSERT INTO `stu` VALUES ('16', '王小丽', '23', '女', '北京', '1000');
INSERT INTO `stu` VALUES ('17', '唐宁', '22', '女', '山东', '2500');
INSERT INTO `stu` VALUES ('18', '唐丽', '21', '女', '北京', '1600');
INSERT INTO `stu` VALUES ('19', '啊永', '23', '男', '北京', '3500');
INSERT INTO `stu` VALUES ('20', '唐玲', '23', '女', '广州', '2500');
INSERT INTO `stu` VALUES ('21', '叙刚', '18', '男', '山西', '3500');
INSERT INTO `stu` VALUES ('22', '王累', '23', '男', '湖北', '4500');
INSERT INTO `stu` VALUES ('23', '赵安', '23', '男', '北京', '1500');
INSERT INTO `stu` VALUES ('24', '关雷', '25', '男', '辽宁', '2500');
INSERT INTO `stu` VALUES ('25', '李字', '22', '男', '北京', '3500');
INSERT INTO `stu` VALUES ('26', '叙安国', '25', '男', '北京', '1500');
INSERT INTO `stu` VALUES ('27', '陈浩难', '23', '女', '北京', '1000');
INSERT INTO `stu` VALUES ('28', '陈明', '22', '女', '山东', '2500');
INSERT INTO `stu` VALUES ('29', '孙丽', '21', '女', '北京', '1600');
INSERT INTO `stu` VALUES ('30', '李治国', '23', '男', '北京', '3500');
INSERT INTO `stu` VALUES ('31', '张娜', '23', '女', '广州', '2500');
INSERT INTO `stu` VALUES ('32', '安强', '18', '男', '山西', '3500');
INSERT INTO `stu` VALUES ('33', '王欢', '23', '男', '湖北', '4500');
INSERT INTO `stu` VALUES ('34', '周天乐', '23', '男', '北京', '1500');
INSERT INTO `stu` VALUES ('35', '关雷', '25', '男', '辽宁', '2500');
INSERT INTO `stu` VALUES ('36', '吴强', '22', '男', '北京', '3500');
INSERT INTO `stu` VALUES ('37', '吴合国', '25', '男', '北京', '1500');
INSERT INTO `stu` VALUES ('38', '正小和', '23', '女', '北京', '1000');
INSERT INTO `stu` VALUES ('39', '吴丽', '22', '女', '山东', '2500');
INSERT INTO `stu` VALUES ('40', '冯含', '21', '女', '北京', '1600');
INSERT INTO `stu` VALUES ('41', '陈冬', '23', '男', '北京', '3500');
INSERT INTO `stu` VALUES ('42', '关玲', '23', '女', '广州', '2500');
INSERT INTO `stu` VALUES ('43', '包利', '18', '男', '山西', '3500');
INSERT INTO `stu` VALUES ('44', '威刚', '23', '男', '湖北', '4500');
INSERT INTO `stu` VALUES ('45', '李永', '23', '男', '北京', '1500');
INSERT INTO `stu` VALUES ('46', '张关雷', '25', '男', '辽宁', '2500');
INSERT INTO `stu` VALUES ('47', '送小强', '22', '男', '北京', '3500');
INSERT INTO `stu` VALUES ('48', '关动林', '25', '男', '北京', '1500');
INSERT INTO `stu` VALUES ('49', '苏小哑', '23', '女', '北京', '1000');
INSERT INTO `stu` VALUES ('50', '赵宁', '22', '女', '山东', '2500');
INSERT INTO `stu` VALUES ('51', '陈丽', '21', '女', '北京', '1600');
INSERT INTO `stu` VALUES ('52', '钱小刚', '23', '男', '北京', '3500');
INSERT INTO `stu` VALUES ('53', '艾林', '23', '女', '广州', '2500');
INSERT INTO `stu` VALUES ('54', '郭林', '18', '男', '山西', '3500');
INSERT INTO `stu` VALUES ('55', '周制强', '23', '男', '湖北', '4500');
```

### 2.创建数据库表

```sql
-- 注释：
-- 单行注释
# 单行注释

/*
多行注释
多行注释
多行注释
*/

# 创建库的语句：
# CREATE DATABASE 库名称;
CREATE DATABASE mmb;
USE mmb;  -- 使用库

# 创建表
/*
CREATE TABLE 表名称(
列名1 类型 约束,
列名2 类型 约束,
……
列名N 类型 约束
)CHARSET=utf8;
*/
# 数据类型：
# 数值：
# int
# float  decimail
# 字符：char / varchar
# 日期时间: date / datetime

CREATE DATABASE IF NOT EXISTS oneday;

USE oneday;

CREATE TABLE dept(
deptno INT PRIMARY KEY AUTO_INCREMENT,
deptname VARCHAR(10) UNIQUE NOT NULL,
loc VARCHAR(20) NOT NULL DEFAULT '北京'
)CHARSET=utf8;

INSERT INTO dept(deptname,loc) VALUES('销售部','北京');
INSERT INTO dept(deptname,loc) VALUES('人事部','上海');
INSERT INTO dept(deptname) VALUES('研发部');
INSERT INTO dept(deptno,deptname,loc) VALUES(4,'外包部','深圳');
```

### 3.主键自增、唯一、非空、默认值

```sql
# 主键约束：
# 唯一、非空、一个表最多一个主键

CREATE TABLE dept(
deptno INT PRIMARY KEY,
dname VARCHAR(10),
loc VARCHAR(20)
)CHARSET=utf8;

INSERT INTO dept VALUES(10,'教研部','北京');
INSERT INTO dept VALUES(20,'学工部','上海');
INSERT INTO dept VALUES(NULL,NULL,NULL);
INSERT INTO dept VALUES(20,NULL,NULL);

# 主键自增：数据类型一般是整数
# PRIMARY KEY 主键  AUTO_INCREMENT 自增
CREATE TABLE dept(
deptno INT PRIMARY KEY AUTO_INCREMENT,
dname VARCHAR(10),
loc VARCHAR(20)
)CHARSET=utf8;

INSERT INTO dept(dname,loc) VALUES('教研部','北京');
INSERT INTO dept(dname,loc) VALUES('学工部','上海');
INSERT INTO dept VALUES(30,'销售部','广州');
INSERT INTO dept(deptno,dname,loc)VALUES(31,'财务部','武汉');

# 唯一约束：
# 值必须是唯一的、一个表可以有多个唯一约束、值可以为空
CREATE TABLE dept(
deptno INT PRIMARY KEY AUTO_INCREMENT,
dname VARCHAR(10) UNIQUE,
loc VARCHAR(20)
)CHARSET=utf8;

INSERT INTO dept(dname,loc) VALUES('教研部','北京');  # 只能执行1次
INSERT INTO dept(dname,loc) VALUES('学工部','上海');  
INSERT INTO dept(dname,loc) VALUES(NULL,'上海');  

# 非空约束
# not null
CREATE TABLE dept(
deptno INT PRIMARY KEY AUTO_INCREMENT,
dname VARCHAR(10) UNIQUE NOT NULL,
loc VARCHAR(20)
)CHARSET=utf8;

INSERT INTO dept(dname,loc) VALUES('教研部','北京');  # 只能执行1次
INSERT INTO dept(dname,loc) VALUES('学工部','上海');  
INSERT INTO dept(dname,loc) VALUES('','上海');  

# NULL : 空
# ''   : 空字符串

CREATE TABLE dept(
deptno INT PRIMARY KEY AUTO_INCREMENT,
dname VARCHAR(10) UNIQUE NOT NULL,
loc VARCHAR(20) NOT NULL DEFAULT ''
)CHARSET=utf8;

INSERT INTO dept(dname,loc) VALUES('教研部','北京'); 
INSERT INTO dept(dname) VALUES('学工部'); 
INSERT INTO dept(dname,loc) VALUES('财务部',NULL); 

# 主键自增、唯一、非空、默认值：
# 主键：唯一、非空、一个表最多只有一个
# 唯一：唯一、可以有多个唯一约束、可以为NULL
# 非空：不能为空
# 默认值：不指定值的情况使用默认值
# 主键 + 自增
# 唯一 + 非空
# 非空 + 默认值
```



### 4.外键约束

```sql
# 外键约束：
# 保证引用的完整性
# RESTRIC：如果子表中存在与父表相关联的记录，则阻止父表的更新或删除操作。这种方式会阻止任何可能导致数据不一致的操作。
# CASCAD：当父表中的记录被删除或更新时，子表中所有相关的记录也会被自动删除或更新。这种方式适用于确保数据的一致性。
# SET DEFAUL：当父表中的记录被更新时，子表中对应的外键字段将被设置为一个默认值。这种方式适用于需要将外键设置为某个默认值的情况。
# SET NUL：当父表中的记录被删除或更新时，子表中对应的记录的外键字段将被设置为NULL。这种方式适用于子表中允许有空值的情况。

# 主表 部门表
CREATE TABLE dept(
deptno INT PRIMARY KEY,
deptname VARCHAR(10),
loc VARCHAR(20)
)CHARSET=utf8;

# 从表 员工表1
CREATE TABLE emp(
empno INT PRIMARY KEY,
empname VARCHAR(20) NOT NULL,
job VARCHAR(10) NOT NULL,
mgr INT,
hiredate DATE,
sal DECIMAL(9,2),
COMM DECIMAL(9,2),
deptno INT,
FOREIGN KEY(deptno) REFERENCES dept(deptno)
)CHARSET=utf8;

INSERT INTO dept VALUES(10,'销售部','北京');
INSERT INTO dept VALUES(20,'人事部','上海');
INSERT INTO dept VALUES(30,'研发部','深圳');
INSERT INTO dept VALUES(40,'外包部','深圳');

INSERT INTO emp VALUES(1000,'张三','经理',NULL,'2000-01-01',100000.00,NULL,20);
INSERT INTO emp VALUES(1001,'李四','销售员',1004,'2014-09-10',6000.00,10000.00,10);
INSERT INTO emp VALUES(1002,'王五','文员',NULL,'2007-10-10',7000.00,NULL,40);
INSERT INTO emp VALUES(1003,'赵六','开发',NULL,'2020-01-01',10000.00,NULL,30);

# 从表 员工表2
CREATE TABLE emp2(
empno INT PRIMARY KEY,
empname VARCHAR(20) NOT NULL,
job VARCHAR(10) NOT NULL,
mgr INT,
hiredate DATE,
sal DECIMAL(9,2),
COMM DECIMAL(9,2),
deptno INT,
FOREIGN KEY(deptno) REFERENCES dept(deptno) ON DELETE CASCADE ON UPDATE CASCADE)CHARSET=utf8;
#ON DELETE CASCADE ON UPDATE CASCADE 代表在主表有删除和更新时，从表会对应的删除记录和更新记录

INSERT INTO emp2 VALUES(1007,'张飞','经理',1009,'2001-09-01',24500.00,NULL,10);
INSERT INTO emp2 VALUES(1008,'诸葛亮','分析师',1004,'2007-04-19',30000.00 ,NULL,20);
INSERT INTO emp2 VALUES(1013,'庞统','分析师',1004,'2001-12-03',30000.00 ,NULL,20);
```

### 5.内外连接

```sql
# 连接查询：把多个表连接成一个表
# 连接查询关键点： 表与表的关系、笛卡尔积+连接条件、内连接和外连接
# 表与表的关系：有关系的表才可以连接
# 一对一： 一个人     	 一个身份号码
# 一对多： 部门(主)      员工(从)
# 多对多： 用户	  订单	 商品

# 笛卡尔积+连接条件
# A={a,b}  B={1,2,3}  --> {a1,a2,a3,b1,b2,b3}  
SELECT * FROM emp,dept;

# 集合的运算符：
# dept  {10,20,30,40}
# emp   {10,20,30}
# 连接： 内连接、外连接

# 交集：{10,20,30}
SELECT * FROM emp,dept WHERE emp.deptno=dept.deptno; 

SELECT * FROM emp AS e,dept AS d WHERE e.`deptno`=d.`deptno`;

SELECT * FROM emp,salgrade;

SELECT * FROM emp,salgrade WHERE sal>=losal AND sal<=hisal;

SELECT * FROM emp AS e,dept AS d,salgrade WHERE e.deptno=d.deptno AND (sal>=losal AND sal<=hisal);

# 交集：{10,20,30}
# 内连接
SELECT * FROM emp AS e
JOIN dept AS d ON
e.`deptno`=d.`deptno`
JOIN salgrade AS s ON
e.sal>=s.losal AND e.sal<=s.hisal;

# 并集：{10,20,30,40}
# 外连接
SELECT * FROM emp RIGHT JOIN dept ON emp.`deptno`=dept.`deptno`; -- 右外连接

SELECT * FROM dept LEFT JOIN emp ON dept.`deptno`=emp.`deptno`; -- 左外连接

-- 补集：{40}
SELECT * FROM emp RIGHT JOIN dept ON emp.`deptno`=dept.`deptno` WHERE emp.`deptno` IS NULL; -- 右外连接

SELECT * FROM dept LEFT JOIN emp ON dept.`deptno`=emp.`deptno` WHERE emp.`deptno` IS NULL; -- 左外连接

# 上级 1  员工 多
# 笛卡尔积 + 条件
# 思考 是否需要使用外连接
SELECT * FROM emp JOIN emp AS e;

SELECT * FROM emp JOIN emp AS e ON emp.mgr=e.`empno`;

SELECT * FROM emp LEFT JOIN emp AS e ON emp.mgr=e.`empno`; -- 左外连接把员工看成左边，有一个员工没有上级，左边表多

SELECT emp.ename,IFNULL(e.`ename`,'') AS mgr_name FROM emp LEFT JOIN emp AS e ON emp.mgr=e.`empno`;

# 表与表的关系：
# 笛卡尔积 + 条件
# 是否需要使用外连接
# 连接后可以看成是一个表

# 把三个表连接起来，不要丢失数据也不要多余数据
SELECT * FROM emp AS e
RIGHT JOIN dept AS d ON
e.`deptno`=d.`deptno`
LEFT JOIN salgrade AS s ON
e.sal>=s.losal AND e.sal<=s.hisal; -- emp和dept连接可能部门会没有员工，所以使用右连接，连接后左边的表比工资范围表大，使用左连接
# WHERE / GROUP BY / HAVING / ORDER BY / LIMIT
```

#### 5.1内外连接查询练习

```sql
# 1.查询所有员工的编号、姓名、部门编号、部门名称和部门地址
SELECT emp.`empno`,emp.`ename`,emp.`deptno`,dept.`dname`,dept.`loc` FROM emp
JOIN dept ON emp.`deptno`=dept.`deptno`;

# 2.查询所有文员的编号、姓名、部门编号、部门名称和部门地址
SELECT emp.`empno`,emp.`ename`,emp.`deptno`,dept.`dname`,dept.`loc` FROM emp
JOIN dept ON emp.`deptno`=dept.`deptno`
WHERE emp.`job`='文员';

# 3.查询所有员工的编号、姓名、部门编号、部门名称和部门地址，结果按照员工的工资升序排序
SELECT emp.`empno`,emp.`ename`,emp.`deptno`,dept.`dname`,dept.`loc` FROM emp
JOIN dept ON emp.`deptno`=dept.`deptno`
ORDER BY emp.`sal`;

# 4.查询工资等级为2级以上的员工姓名、部门名称、工资和工资等级
SELECT emp.`ename`,dept.`dname`,emp.`sal`,salgrade.`grade` FROM emp
JOIN dept ON emp.`deptno`=dept.`deptno`
JOIN salgrade ON sal>=losal AND sal<=hisal
WHERE grade>2;

# 5.查询每个部门的部门名称和部门员工人数
SELECT dname,COUNT(emp.`empno`) AS total FROM emp
RIGHT JOIN dept ON emp.`deptno`=dept.`deptno`
GROUP BY dept.`deptno`;

# 6.查询每个部门的部门名称和部门员工人数，结果只显示人数大于3人的部门名称和部门员工人数
SELECT dname,COUNT(emp.`empno`) AS total FROM emp
JOIN dept ON emp.`deptno`=dept.`deptno`
GROUP BY dept.`deptno`
HAVING total>3;

# 7.查询工资等级为2级的员工姓名和工资等级
SELECT emp.`ename`,salgrade.`grade` FROM emp
JOIN salgrade ON sal>=losal AND sal<=hisal
WHERE grade=2;

# 8.查询所有员工姓名、上级领导姓名、部门名称、和工资等级
SELECT emp.`ename`,IFNULL(e.`ename`,'') AS mgr_name,dept.`dname`,salgrade.`grade` FROM emp
JOIN dept ON emp.`deptno`=dept.`deptno`
JOIN salgrade ON sal>=losal AND sal<=hisal
LEFT JOIN emp AS e ON emp.`mgr`=e.`empno`;
```

### 6.子查询

```sql
# 1.查询工资高于殷天正并且低于诸葛亮的员工
SELECT ename,sal FROM emp WHERE sal>(SELECT sal FROM emp WHERE ename='殷天正')
AND sal<(SELECT sal FROM emp WHERE ename='诸葛亮');

# 2.查询工资最高的员工姓名、工作和工资
SELECT ename,job,sal FROM emp
WHERE sal=(SELECT MAX(sal) FROM emp);

# 3.查询工资最低的员工姓名、工作和工资
SELECT ename,job,sal FROM emp
WHERE sal=(SELECT MIN(sal) FROM emp);

# 4.查询"学工部"工资最高的员工姓名、工作和工资
SELECT ename,job,sal FROM emp
JOIN dept ON emp.`deptno`=dept.`deptno`
WHERE dept.`dname`='学工部'
AND sal=(SELECT MAX(sal) FROM emp
JOIN dept ON emp.`deptno`=dept.`deptno`
WHERE dept.`dname`='学工部')

# 5.查询"学工部"工资最高的员工姓名、工作、工资、部门名称和部门人数
SELECT ename,job,sal,dname,COUNT(empno) AS total FROM emp
JOIN dept ON emp.`deptno`=dept.`deptno`
WHERE dept.`dname`='学工部'
AND sal=(SELECT MAX(sal) FROM emp
JOIN dept ON emp.`deptno`=dept.`deptno`
WHERE dept.`dname`='学工部')

# 6.查询与"刘备"或"诸葛亮"从事相同工作的员工
SELECT ename,job FROM emp
WHERE job IN (SELECT job FROM emp WHERE ename='刘备' OR ename='诸葛亮');

# 7.查询入职日期早于上级的员工编号、姓名、工资
SELECT emp.`empno`,emp.`ename`,emp.sal FROM emp
LEFT JOIN emp AS e
ON emp.`mgr`=e.`empno`
WHERE emp.`hiredate` < e.`hiredate`;

# 8.查询上级为"刘备"的员工
SELECT emp.`ename`,emp.`mgr`,e.`ename` FROM emp
LEFT JOIN emp AS e
ON emp.`mgr`=e.`empno`
WHERE e.`ename`='刘备';

# 9.查询工资最高员工所在的部门名称
SELECT emp.`ename`,dept.`dname` FROM emp
JOIN dept ON emp.`deptno`=dept.`deptno`
WHERE sal=(SELECT MAX(sal) FROM emp)

# 10.查询没有员工的部门名称
SELECT dept.`dname` FROM emp
RIGHT JOIN dept ON emp.`deptno`=dept.`deptno`
WHERE emp.`deptno` IS NULL;
```

> [!TIP]
> 子查询7 8 10没有使用子查询方法，可自行使用
