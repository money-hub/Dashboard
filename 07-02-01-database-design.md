# 1. ER图

![ER图](./images/ER.png)



# 2. 数据库物理模型

![数据库物理模型](./images/数据库物理模型.png)

> 相应代码

```mysql

# 创建相应的数据库
create database if not exists MoneyDodo;

use MoneyDodo;

# 用户
create table if not exists user (
	id varchar(20) primary key COMMENT '学号',
    name varchar(20) not null COMMENT '姓名',
    password varchar(20) not null COMMENT '密码',
    introduction text COMMENT '个人简介',
    balance double COMMENT '余额',
    icon MEDIUMBLOB COMMENT '头像',
    phone varchar(11) COMMENT '电话号码',
    creditScore int COMMENT '信用分数',
    email varchar(20) COMMENT '邮箱',
    cardPic MEDIUMBLOB COMMENT '学生证',
	identification bool default false COMMENT '认证'
);

# 管理员
create table if not exists admin (
    name varchar(20) not null COMMENT '姓名',
    password varchar(20) not null COMMENT '密码'
);

# 企业
create table if not exists enterprise (
    name varchar(20) not null COMMENT '姓名',
    password varchar(20) not null COMMENT '密码'
);

# 任务
create table if not exists task (
	taskId int AUTO_INCREMENT primary key COMMENT '任务id',
    taskType varchar(20) not null COMMENT '任务类型',
    taskFrom varchar(20) not null COMMENT '发布者',
    recipient text COMMENT '接收者',
    taskLimit text COMMENT '任务限制',
    releaseTime text not null COMMENT '发布时间',
    cutoffTime text COMMENT '截至时间',
    rewardAmount double not null  COMMENT '赏金金额',
    taskStatus varchar(20) COMMENT '任务状态'
);
```
