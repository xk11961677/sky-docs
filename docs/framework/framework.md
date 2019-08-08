## 介绍
### Sky Cloud 
[![Build Status](https://travis-ci.org/xk11961677/framework.svg?branch=master)](https://travis-ci.org/xk11961677/framework)
[![license](https://img.shields.io/badge/license-MIT-ff69b4.svg)](https://mit-license.org/license.html)

### 代码结构
- [framework-bom](framework-bom) framework项目jar包版本依赖管理
    -  版本号：<主版本>.<次版本>.<增量版本>-<代号>
    -  直接修改<revision>1.0.0-SNAPSHOT</revision>属性版本 
- [framework-generator-plugin](framework-generator-plugin) 代码生成器插件
- [framework-web](framework-web) Spring Boot Web 脚手架依赖
- [framework-model](framework-model) 公共DTO实体与分页实体
- [framework-integrate](framework-integrate) 整合其他三方库,如netty、spark等
    -  [framework-integrate-validator](framework-integrate/framework-integrate-validator)  业务参数验证器,使用方法请读本项目[readme.md](framework-integrate/framework-integrate-validator/readme.md)
    -  [framework-integrate-redis](framework-integrate/framework-integrate-redis)  redis,使用方法请读本项目[readme.md](framework-integrate/framework-integrate-redis/readme.md)
    -  [framework-integrate-rocketmq](framework-integrate/framework-integrate-rocketmq)  mq,使用方法请读本项目[readme.md](framework-integrate/framework-integrate-rocketmq/readme.md)
    -  [framework-integrate-job](framework-integrate/framework-integrate-job)  分布式定时任务,使用方法请读本项目[readme.md](framework-integrate/framework-integrate-job/readme.md)
- [framework-util](framework-util) 工具类
    -  [framework-util-common](framework-util/framework-util-common)  公共工具类包
    -  [framework-util-threadpool](framework-util/framework-util-threadpool)  线程池工具类,使用方法请读本项目[readme.md](framework-util/framework-util-threadpool/readme.md)

## 详细功能
### util工具包
#### common包
1): 引入如下包
```
<dependency>
    <groupId>com.sky.framework</groupId>
    <artifactId>framework-util-common</artifactId>
</dependency>
```
2): 配置自定义属性（可省略）

3): 代码编写方式
![图1](images/threadpool-1.png)
![图1](images/threadpool-2.png)
#### threadpool包
1): 引入如下包
```
<dependency>
    <groupId>com.sky.framework</groupId>
    <artifactId>framework-util-threadpool</artifactId>
</dependency>
```
2): 配置自定义属性（可省略）
IDEA下,在yml文件中填写 asyncthreadpool 会自动提示配置项
请根据自己模块定制化配置(如果需要)
3): 代码编写方式
![图1](images/threadpool-1.png)
![图1](images/threadpool-2.png)

### integrate包