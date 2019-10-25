# 商品管理服务用户手册

## 引言

### 编写目的

为商品管理服务接入方开发人员提供一个规范化的接口协议，更方便地进行业务整合嵌入。

### 背景

商品管理服务使用http接口对外提供服务，文档中展示使用feign 进行http调用，业务方也可以选择其他htpp组件进行接入
### 定义

## 概述

商品管理服务使用http接口对外提供服务，文档中展示使用feign 进行http调用，业务方也可以选择其他htpp组件进行接入
### 产品简介

### 什么是商品管理
维护客户开票使用的商品以及税编信息，并且维护供应商协同商品与客户商品映射关系

### 产品优势

+ 提供http接口与sdk方式接入
+ 全面支持各业务线拆票需求
+ 支持按使用量弹性伸缩扩展
+ 性能优异, 单节点可支持3000qps
+ 按量付费，并提供折扣价套餐

### 产品功能
+ 商品管理增删改查功能
+ 支商品类型管理功能
+ 税编管理功能



## 微服务接入方式
### 1.Jar包引入

<!--DOCUSAURUS_CODE_TABS-->
<!--pom-->
```pom
<dependency> 
  <groupId>xf-bm-xplat-msg</groupId>
  <artifactId>goods-api</artifactId>
  <version>1.0-SNAPSHOT</version>
</dependency>
```
<!--END_DOCUSAURUS_CODE_TABS-->

### 2.创建feign客户端
<!--DOCUSAURUS_CODE_TABS-->
<!--Java-->
```java
//url指定的地址为fat外网地址，建议业务方配置内网地址访问
@FeignClient(name = "goods-service", url = "http://goods-manger-fat.phoenix-t.xforceplus.com")
public interface GoodsClient extends GoodsApi {
    }
```
<!--END_DOCUSAURUS_CODE_TABS-->

### 3.使用客户端
<!--DOCUSAURUS_CODE_TABS-->
<!--Java-->
```java
@Autowired
private GoodsClient goodsClient;
//调用GoodsClient对象方法即可发起对应接口的调用
```
<!--END_DOCUSAURUS_CODE_TABS-->


### 返回码清单
原有接口

|  code  | 描述 | 
|  :---- |:----|
|GDCTZZ0001|调用成功|
| GDCTZZ0400 |调用接口参数错误，response中有错误参数详情|
| GDCTZZ0500 |系统内部错误，联系中台解决|

## 压测报告


## 联调环境

## 参考资料

[《商品管理prd》](https://wiki.xforceplus.com/pages/viewpage.action?pageId=33460523&src=contextnavpagetreemode)
[《商品管理erd》](https://wiki.xforceplus.com/pages/viewpage.action?pageId=30028450&src=contextnavpagetreemode)

## 联系方式
tower@xforceplus.com