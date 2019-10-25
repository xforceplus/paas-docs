# 通知中心接口列表


<a name="overview"></a>
## 概览

### 版本信息
*版本* : 1.0.0


### URI scheme
*域名* : nofitication-fat-svc.phoenix-t.xforceplus.com  
*基础路径* : /


### 标签

* message-controller : Message Controller




<a name="paths"></a>
## 路径

<a name="sendmessageusingpost"></a>
### 发送消息通知
```
POST /{tenantId}/message/v1/messages
```


#### 参数

|类型|名称|说明|类型|
|---|---|---|---|
|**Header**|**x-userinfo**  <br>*可选*|用户信息|string|
|**Path**|**tenantId**  <br>*必填*|tenantId|integer (int64)|
|**Body**|**messageInfo**  <br>*必填*|messageInfo|[MessageInfo](#messageinfo)|


#### 响应

|HTTP代码|说明|类型|
|---|---|---|
|**200**|OK|[BaseResponse](#baseresponse)|
|**201**|Created|无内容|
|**401**|Unauthorized|无内容|
|**403**|Forbidden|无内容|
|**404**|Not Found|无内容|


#### 消耗

* `application/json;charset=UTF-8`


#### 生成

* `application/json;charset=UTF-8`


#### 标签

* message-controller


<a name="querymessagesusingget"></a>
### 查询消息列表
```
GET /{tenantId}/message/v1/messages/{appId}/my-messages
```


#### 参数

|类型|名称|说明|类型|
|---|---|---|---|
|**Header**|**x-userinfo**  <br>*可选*|用户信息|string|
|**Path**|**appId**  <br>*必填*|产品线id|string|
|**Path**|**tenantId**  <br>*必填*|租户id|string|
|**Query**|**page**  <br>*必填*|页码，从1开始|string|
|**Query**|**queryType**  <br>*必填*|查询类型，SINGLE=个人消息，GLOBAL=全局消息|enum (SINGLE, GLOBAL)|
|**Query**|**size**  <br>*必填*|每页数量，不能超过200|string|
|**Query**|**sortBy**  <br>*可选*|排序字段，例如+createTime表示按时间升序，-createTime标识按时间降序|string|
|**Query**|**tag**  <br>*可选*|消息标签|string|


#### 响应

|HTTP代码|说明|类型|
|---|---|---|
|**200**|OK|[BaseResponse«MessagePage»](#6af153bad5107c5dd44db9271f001ee1)|
|**401**|Unauthorized|无内容|
|**403**|Forbidden|无内容|
|**404**|Not Found|无内容|


#### 生成

* `application/json;charset=UTF-8`


#### 标签

* message-controller


<a name="queryhasnewmsgusingget"></a>
### 轮询是否有新消息
```
GET /{tenantId}/message/v1/messages/{appId}/new-messages
```


#### 参数

|类型|名称|说明|类型|
|---|---|---|---|
|**Header**|**x-userinfo**  <br>*可选*|用户信息|string|
|**Path**|**appId**  <br>*必填*|产品线id|string|
|**Path**|**tenantId**  <br>*必填*|租户id|string|
|**Query**|**lastMsgId**  <br>*必填*|最新消息id|string|
|**Query**|**queryType**  <br>*必填*|查询类型，SINGLE=个人是否有最新消息，GLOBAL=全局是否有新消息|enum (SINGLE, GLOBAL)|


#### 响应

|HTTP代码|说明|类型|
|---|---|---|
|**200**|OK|[BaseResponse](#baseresponse)|
|**401**|Unauthorized|无内容|
|**403**|Forbidden|无内容|
|**404**|Not Found|无内容|


#### 生成

* `\*/*`


#### 标签

* message-controller


<a name="querymessageusingget"></a>
### 查询消息详情
```
GET /{tenantId}/message/v1/messages/{messageId}
```


#### 参数

|类型|名称|说明|类型|
|---|---|---|---|
|**Header**|**x-userinfo**  <br>*可选*|用户信息|string|
|**Path**|**messageId**  <br>*必填*|消息id|string|
|**Path**|**tenantId**  <br>*必填*|租户id|string|


#### 响应

|HTTP代码|说明|类型|
|---|---|---|
|**200**|OK|[BaseResponse«MessageDetail»](#a216230354fcc71d8520f133e3c3cdd1)|
|**401**|Unauthorized|无内容|
|**403**|Forbidden|无内容|
|**404**|Not Found|无内容|


#### 生成

* `application/json;charset=UTF-8`


#### 标签

* message-controller


<a name="restatususingput"></a>
### 更新消息为已读状态
```
PUT /{tenantId}/message/v1/messages/{messageId}/status
```


#### 参数

|类型|名称|说明|类型|
|---|---|---|---|
|**Header**|**x-userinfo**  <br>*可选*|用户信息|string|
|**Path**|**messageId**  <br>*必填*|消息id|string|
|**Path**|**tenantId**  <br>*必填*|租户id|string|


#### 响应

|HTTP代码|说明|类型|
|---|---|---|
|**200**|OK|[BaseResponse](#baseresponse)|
|**201**|Created|无内容|
|**401**|Unauthorized|无内容|
|**403**|Forbidden|无内容|
|**404**|Not Found|无内容|


#### 消耗

* `application/json`


#### 生成

* `application/json;charset=UTF-8`


#### 标签

* message-controller




<a name="definitions"></a>
## 定义

<a name="baseresponse"></a>
### BaseResponse

|名称|类型|
|---|---|
|**code**  <br>*可选*|string|
|**message**  <br>*可选*|string|
|**result**  <br>*可选*|object|


<a name="a216230354fcc71d8520f133e3c3cdd1"></a>
### BaseResponse«MessageDetail»

|名称|类型|
|---|---|
|**code**  <br>*可选*|string|
|**message**  <br>*可选*|string|
|**result**  <br>*可选*|[MessageDetail](#messagedetail)|


<a name="6af153bad5107c5dd44db9271f001ee1"></a>
### BaseResponse«MessagePage»

|名称|类型|
|---|---|
|**code**  <br>*可选*|string|
|**message**  <br>*可选*|string|
|**result**  <br>*可选*|[MessagePage](#messagepage)|


<a name="messagedetail"></a>
### MessageDetail

|名称|说明|类型|
|---|---|---|
|**content**  <br>*可选*|内容|string|
|**createTime**  <br>*可选*|创建时间|string (date-time)|
|**id**  <br>*可选*|消息id|integer (int64)|
|**readTime**  <br>*可选*|阅读时间|string (date-time)|
|**status**  <br>*可选*|状态，0=未读，1=已读|integer (int32)|
|**tags**  <br>*可选*||< string > array|
|**title**  <br>*可选*|标题|string|
|**url**  <br>*可选*|链接|string|


<a name="messageinfo"></a>
### MessageInfo

|名称|说明|类型|
|---|---|---|
|**appId**  <br>*可选*|产品线id|integer (int64)|
|**content**  <br>*可选*|消息内容|string|
|**receiverIds**  <br>*可选*|接收人id列表, scope=[SINGLE]时必填|< integer (int64) > array|
|**scope**  <br>*可选*|消息范围，GLOBAL=全局消息，APP_GLOBAL=产品线内消息，SINGLE=个人消息|enum (GLOBAL, APP_GLOBAL, SINGLE)|
|**senderId**  <br>*可选*|发送人id, 当scope=[GLOBAL,APP_GLOBAL]时必填|integer (int64)|
|**tags**  <br>*可选*|标签|< string > array|
|**title**  <br>*可选*|消息标题|string|
|**type**  <br>*可选*|类型, 0 系统消息 1 业务消息 2 用户消息|integer (int32)|
|**url**  <br>*可选*|附件下载链接|string|


<a name="messagepage"></a>
### MessagePage

|名称|说明|类型|
|---|---|---|
|**messages**  <br>*可选*|消息列表|< [MessageDetail](#messagedetail) > array|
|**total**  <br>*可选*||integer (int64)|





