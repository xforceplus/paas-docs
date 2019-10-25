# 拆票服务用户手册

## 引言

### 编写目的

本协议适用于拆票服务与第三方接入平台间的行为、数据及事件的交互与传递。 本协议承载于 HTTP 协议，严格遵守 HTTP 协议规范。

### 背景

本协议适用于拆票服务与第三方接入平台间的行为、数据及事件的交互与传递。 本协议承载于 HTTP 协议，严格遵守 HTTP 协议规范。

### 定义

## 概述

接入拆票服务提供两种方式对外服务，
一种为http接口，如果使用http接口方式对接需要联系中台配置租户相关属性，
一种为sdk，该方式仅提供给无法访问公司PaaS平台的属地化应用，禁止其他任何产品线在未经批准的情况下使用SDK，违者全公司通报批评，并责令其改正。
接入步骤中展示使用spring feign组件进行对接，业务方可以替换成其他http组件发起http请求，没有限制

### 产品简介

### 什么是拆票服务
拆票服务是由服务下沉团队提供的订单到预制发票的转换服务，从各个业务线中创建预制发票业务需求演变而来

### 产品优势

+ 提供http接口与sdk方式接入
+ 全面支持各业务线拆票需求
+ 支持按使用量弹性伸缩扩展
+ 性能优异, 单节点可支持3000qps
+ 按量付费，并提供折扣价套餐

### 产品功能
为各业务团队提供拆票功能，主要功能点：
+ 支持按限额创建预制发票
+ 支持发票备注自定义
+ 支持红蓝票创建
+ 支持红字业务单拆分


## 产品定价

### 计费方式
|  服务可用性  | 赔偿金额 | 定价 |
|  :----  | :----  |:---- |
| 拆票服务  | 单价|0.005元/张 |
| 拆票服务 | 套餐 | 100元/20,000张、1,000元/230,000张(85折)、10,000元/2,500,000张(8折)、100,000元/28,000,000张(7折)。 |
| 拆票服务  | 优惠政策 | 公司内部产品线接入前三位，按照所购套餐价8折计费，且提供免费资深工程师咨询服务，并协助接入；成功拆分预制发票则收费，未成功拆分预制发票则不收费；|


### 赔付方案

如服务可用性低于98%，可按照下表中的标准获得赔偿，且赔偿总额不超过在未达到服务可用性承诺期间内的客户实际支付的服务费。
赔偿的服务费作为一下计费周期的费用抵扣。

|  服务可用性  | 赔偿金额 | 
|  :----  | :----  |
| 低于99%但等于或高于98%  | 10%|
| 低于98%但高于或等于95% | 20% |
| 低于95% | 30% |

## 接口清单

http://bill-split-dev.phoenix-t.xforceplus.com/swagger-ui.html
接口清单中有两个接口，业务需要对接的是pre-invoice-generate-controller，synchronization-pre-invoice-generate-controller 接口为同步测试接口，可以实时获取拆票结果用于调试，生产环境不提供

## 接入步骤

### 微服务接入方式

### 1.Jar包引入

<!--DOCUSAURUS_CODE_TABS-->
<!--pom-->
```pom
<dependency>  
  <groupId>xf-bm-xplat-msg</groupId>
  <artifactId>split-client-api</artifactId>
  <version>1.0.6</version>
</dependency>
```
<!--END_DOCUSAURUS_CODE_TABS-->

### 2.创建feign客户端
<!--DOCUSAURUS_CODE_TABS-->
<!--Java-->
```java
//url指定的地址为fat外网地址，建议业务方配置内网地址访问
@FeignClient(name = "bill-split-service", url = "http://bill-split-fat.phoenix-t.xforceplus.com")
public interface PreInvoiceGenerateClient extends PreInvoiceGenerateApi {
}
```
<!--END_DOCUSAURUS_CODE_TABS-->

### 3.使用客户端
<!--DOCUSAURUS_CODE_TABS-->
<!--Java-->
```java
//拆票服务提供的http接口是一个异步接口，收到拆票请求之后会马上响应一个唯一流水号给调用者，拆票服务在后台进行异步拆票，拆票完成之后会通过回调服务通知给业务方

@Autowired
private PreInvoiceGenerateApi preInvoiceGenerateApi;

long tenantId = 10;//中台提供
long appId  = 10;//中台提供

CreatePreInvoiceParam param = new CreatePreInvoiceParam();//拆票参数，字段释义可以查看swagger

BaseResponse<String> response =  preInvoiceGenerateApi.sendSplitMsg(tenantId, appId, param);
if ("BSCTZZ0001".equals(response.getCode())) {//发送拆票请求成功
    String txId = response.getResult();//请求流水号，代表唯一一次拆票请求，拆票服务异同通知时会带上
}
```
<!--END_DOCUSAURUS_CODE_TABS-->

### 4.回调接口说明
**1.业务方需要提供一个http回调接口，用于接收拆票结果，method=post, requestBody 结构如下**
<!--DOCUSAURUS_CODE_TABS-->
<!--json-->
```json
{
	"code": "CPTNCB0001",
	"message": "",
	"result": {
		"serialNo": "12345678lkjflakdjf",
		"data": {
			"ossUrl": "",//拆票结果下载地址
			"compress": "true",//是否压缩，true=是，false=否，如果是被压缩的，需要解压缩使用
			"txId": ""//流水号，与发送拆票请求时返回的流水号对应
		}
	}
}
```
<!--END_DOCUSAURUS_CODE_TABS-->

**2.对于业务方提供的回调接口必须在2s内响应200状态码，如果在2s内未响应200状态码回调系统则认为失败，会进行N次重试**

**3.拆票服务在完成拆票之后会通过调用业务方提供的回调接口返回拆票结果**

**4.业务方在回调接口中获取到的ossUrl地址从oss下载拆票结果，拆票结果格式对应的mode为split-client-api中的SplitResponse类**

**5.SplitResponse中code为 BSCTZZ0001 代表拆票成功，其他则为失败，失败信息在message字段中**

**6.通过oss获取拆票结果代码如下**
<!--DOCUSAURUS_CODE_TABS-->
<!--java-->
```java
RestTemplate restTemplate = new RestTemplate();

String ossUrl = "http://tower001-bucket001-fat.oss-cn-hangzhou.aliyuncs.com/2019/7/17/4f63ff28fb014c3c989af48b816fcd0a?Expires=1563437913&OSSAccessKeyId=LTAIMZA4AkW9trwl&Signature=jADGOE%2BIz%2FNZZRF0zuejdKQVXHg%3D";

URI uri = new URI(ossUrl);

ResponseEntity<byte[]> response = restTemplate.getForEntity(uri, byte[].class);

boolean compress = true;

byte[] splitData = response.getBody();
if (compress) {
    Inflater decompresser = new Inflater();
    decompresser.setInput(splitData);
    byte[] data = new byte[1024];
    int length = 0;
    try (ByteArrayOutputStream bos = new ByteArrayOutputStream(splitData.length)){
        while (!decompresser.finished()) {
            length = decompresser.inflate(data);
            bos.write(data, 0, length);
        }
        decompresser.end();
        splitData = bos.toByteArray();
    }
}
SplitResponse splitResponse = JSON.parseObject(splitData, SplitResponse.class);
```
<!--END_DOCUSAURUS_CODE_TABS-->

### SDK接入方式

### 1.Jar包引入
<!--DOCUSAURUS_CODE_TABS-->
<!--pom-->
```pom
<dependency>
  <groupId>xf-bm-xplat-msg</groupId>
  <artifactId>split-core</artifactId>
  <version>1.0.6</version>
</dependency>
```
<!--END_DOCUSAURUS_CODE_TABS-->

### 2.代码示例
<!--DOCUSAURUS_CODE_TABS-->
<!--Java-->
```java
private Bill2PreInvoiceService bill2PreInvoiceService;

//单据信息
BillInfo billInfo = new BillInfo();
//拆票规则
SplitRule rule = new SplitRule();
//规则code, 无特殊配置默认default即可
String ruleCode = "default";

//调用拆票方法，生成预制发票
List<SplitPreInvoiceInfo> preInvoiceInfoList = bill2PreInvoiceService.createPreInvoiceFromBill(billInfo, rule, ruleCode);
```
<!--END_DOCUSAURUS_CODE_TABS-->

### 3.sdk升级 release notes

1.0.6 自定义备注长度
1.0.5 自定义备注长度
1.0.4 明细备注去重
1.0.3 拆票限额check
1.0.2 预制发票明细添加priceMothed
1.0.1 非红冲发票的红字业务单不可以打印销货清单


### 返回码清单
|  code  | 描述 | 
|  :----   |:----|
|BSCTZZ0001 | 调用成功 |
| BSCTZZ0400 | 调用接口参数错误，response中有错误参数详情|
|BSCTZZ0500 | 系统内部错误，联系中台解决 |

## 压测报告



## 联调环境

详见[《服务下沉环境信息》](https://wiki.xforceplus.com/pages/viewpage.action?pageId=30025683)中FAT环境配置
| 产品线 | routingKey | tenantId | appId |
|  :----   |:----|:----|:----|
| 协同产品线 | zt_xtcpx |100|100|
| 标准行业线 | zt_tycpx|200|200|
|标准行业线sit环境| zt_tycpx_sit |200|200|

## 联系方式
tower@xforceplus.com