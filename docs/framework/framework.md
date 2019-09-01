## 介绍
### framework
[![Build Status](https://travis-ci.org/xk11961677/framework.svg?branch=master)](https://travis-ci.org/xk11961677/framework)
[![license](https://img.shields.io/badge/license-mit-ff69b4.svg)](https://mit-license.org/license.html)
[![springboot](https://img.shields.io/badge/springboot-2.1.4.RELEASE-orange.svg)](https://spring.io/projects/spring-boot)
![Gitter](https://img.shields.io/gitter/room/sky-docs/community)
![version](https://img.shields.io/badge/version-1.0.0-blueviolet.svg)
![helloworld](https://img.shields.io/badge/hello-world-blue)

### 版本管理
    - 版本号：<主版本>.<次版本>.<增量版本>-<代号>
    - 直接修改<revision>1.0.0-SNAPSHOT</revision>属性版本 

### 代码结构
```
│
├─framework----------------------------父项目，公共依赖
│  │
│  ├─framework-bom-----------------第三方jar包版本依赖管理
│  │
│  ├─framework-dependencies------------------整体对外jar版本
│  │
│  ├─framework-generator-plugin-----------------代码生成器依赖的jar(非web站点形式)
│  │
│  ├─framework-rpc--------------------------------rpc 项目(暂时仅为教学使用)
│  │
│  ├─framework-dao------------------整合数据库访问(hive、hbase等)
│  │
│  ├─framework-web------------------Spring Boot Web 脚手架依赖
│  │
│  ├─framework-model------------------公共实体
│  │
│  ├─framework-integrate------------------整合其他三方库,如netty、spark等
│  │  │
│  │  ├─framework-integrate-validator------------------业务参数验证器(基于fluent-validator)
│  │  │
│  │  ├─framework-integrate-redis------------------缓存redisson与lettuce,支持springboot cache
│  │  │
│  │  ├─framework-integrate-rocketmq------------------rocketmq
│  │  │
│  │  ├─framework-integrate-job------------------分布式定时任务
│  │  │
│  │  ├─framework-integrate-canel------------------增量同步mysql binlog
│  │  │
│  ├─framework-util------------------工具类
│  │  │
│  │  ├─framework-util-common------------------公共工具类包
│  │  │
│  │  ├─framework-util-oss------------------对象资源存储
│  │  │
│  │  ├─framework-util-threadpool------------------线程池工具类
│  │  │
│  │  │
│  ├─framework-xxx---------------------------------------------------------
│  │
```

## 详细功能

### framework-util
#### common
1): 引入如下包
```
<dependency>
    <groupId>com.sky.framework</groupId>
    <artifactId>framework-util-common</artifactId>
</dependency>
```
2): 功能

一致性hash、LRUCache、钉钉通知、加解密、http client
id生成器、location、短信、tuple、validation、xml等


#### oss
1): 引入如下包
```
<dependency>
    <groupId>com.sky.framework</groupId>
    <artifactId>framework-util-oss</artifactId>
</dependency>
```
2): 配置自定义属性（可省略）
```
oss:
  aliyun:
      access-key-id: xxxx
      access-key-secret: xxxx
      bucketName: sky
      endpoint: oss-cn-hangzhou.aliyuncs.com
  callbackUrl: http://127.0.0.1:8904/open/oss/callback
  dir-prefix: sky/
  strategy: aliyun
  url-prefix: http://sky.oss-cn-hangzhou.aliyuncs.com
```

3): 代码编写方式

请查看[skycloud-base-upload](https://github.com/xk11961677/skycloud-base/tree/master/skycloud-base-upload)


#### threadpool
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
<div >
<img src="/framework/images/threadpool-1.png" height="200px" width="500px" alt="线程池默认处理器"/>
</div>
<div >
<img src="/framework/images/threadpool-2.png" height="200px" width="500px" alt="线程池默认处理器"/>
</div>

### framework-integrate