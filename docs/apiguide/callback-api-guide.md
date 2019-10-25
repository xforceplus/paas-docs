# 回调服务接口样式


<a name="overview"></a>
## 概览
Api Documentation


### 版本信息
*版本* : 1.0


### 许可信息
*许可证* : Apache 2.0  
*许可网址* : http://www.apache.org/licenses/LICENSE-2.0  
*服务条款* : urn:tos


### URI scheme
*域名* : gw.cb.phoenix-t.xforceplus.com  
*基础路径* : /


### 标签

* Cooperation : the callbacks API
* feedback-api-controller : the feedback API




<a name="paths"></a>
## 路径

<a name="outfeedbackusingpost"></a>
### 外部系统回执接口
```
POST /message/v1/feedback/{channelId}
```


#### 参数

|类型|名称|说明|类型|
|---|---|---|---|
|**Path**|**channelId**  <br>*必填*|channelId|string|


#### 响应

|HTTP代码|说明|类型|
|---|---|---|
|**200**|统一返回|object|
|**201**|Created|无内容|
|**401**|Unauthorized|无内容|
|**403**|Forbidden|无内容|
|**404**|Not Found|无内容|


#### 消耗

* `application/json`


#### 生成

* `application/json`


#### 标签

* Cooperation


<a name="cooperationusingpost"></a>
### 租户回调接口
```
POST /{tenantId}/message/v1/callbacks
```


#### 参数

|类型|名称|说明|类型|
|---|---|---|---|
|**Path**|**tenantId**  <br>*必填*|租户ID|string|
|**Body**|**cooperationParams**  <br>*必填*|封装发送回调需要的参数|[CooperationParams](#cooperationparams)|


#### 响应

|HTTP代码|说明|类型|
|---|---|---|
|**200**|统一返回|[Response](#response)|
|**201**|Created|无内容|
|**401**|Unauthorized|无内容|
|**403**|Forbidden|无内容|
|**404**|Not Found|无内容|


#### 消耗

* `application/json`


#### 生成

* `application/json`


#### 标签

* Cooperation




<a name="definitions"></a>
## 定义

<a name="cooperationparams"></a>
### CooperationParams
回调参数集合


|名称|说明|类型|
|---|---|---|
|**content**  <br>*可选*|回调body报文|string|
|**properties**  <br>*可选*|参数属性|[CooperationProperties](#cooperationproperties)|


<a name="cooperationproperties"></a>
### CooperationProperties
参数属性


|名称|说明|类型|
|---|---|---|
|**appKey**  <br>*可选*|客户申请的应用标识|string|
|**ext**  <br>*可选*|扩展header参数|[CooperationPropertiesExtParam](#cooperationpropertiesextparam)|
|**rule**  <br>*可选*|规则代码|string|


<a name="cooperationpropertiesextparam"></a>
### CooperationPropertiesExtParam
扩展属性参数


|名称|说明|类型|
|---|---|---|
|**attachment**  <br>*可选*|邮件附件链接地址，email类型可选|string|
|**destination**  <br>*可选*|规则为邮箱则是邮箱地址，为短信则为手机号，http可不传|string|
|**subject**  <br>*可选*|邮件主题，email类型必传|string|


<a name="response"></a>
### Response

|名称|类型|
|---|---|
|**code**  <br>*可选*|string|
|**message**  <br>*可选*|string|
|**result**  <br>*可选*|object|





