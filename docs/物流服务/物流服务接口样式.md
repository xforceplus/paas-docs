# 物流服务接口样式


<a name="overview"></a>
## 概览
物流服务 API


### 版本信息
*版本* : 1.0.0


### URI scheme
*域名* : logistics-service-fat.phoenix-t.xforceplus.com  
*基础路径* : /


### 标签

* logist-controller : Logist Controller
* logistics : 物流服务API




<a name="paths"></a>
## 路径

<a name="getexpresslistusingget"></a>
### getExpressList
```
GET /enterprise/v1/logistics/expressList
```


#### 参数

|类型|名称|说明|类型|
|---|---|---|---|
|**Header**|**x-userinfo**  <br>*可选*|用户信息|string|


#### 响应

|HTTP代码|说明|类型|
|---|---|---|
|**200**|OK|[Resp](#resp)|
|**401**|Unauthorized|无内容|
|**403**|Forbidden|无内容|
|**404**|Not Found|无内容|


#### 生成

* `\*/*`


#### 标签

* logist-controller


<a name="getlogistdetailusingget"></a>
### getLogistDetail
```
GET /enterprise/v1/logistics/logistDetail
```


#### 参数

|类型|名称|说明|类型|
|---|---|---|---|
|**Header**|**appId**  <br>*必填*|appId|string|
|**Header**|**timestamp**  <br>*必填*|timestamp|string|
|**Header**|**x-userinfo**  <br>*可选*|用户信息|string|
|**Query**|**expressCode**  <br>*可选*|expressCode|string|
|**Query**|**parcelNo**  <br>*可选*|parcelNo|string|


#### 响应

|HTTP代码|说明|类型|
|---|---|---|
|**200**|OK|[Resp](#resp)|
|**401**|Unauthorized|无内容|
|**403**|Forbidden|无内容|
|**404**|Not Found|无内容|


#### 生成

* `\*/*`


#### 标签

* logist-controller


<a name="orderlogistusingpost"></a>
### orderLogist
```
POST /enterprise/v1/logistics/order
```


#### 参数

|类型|名称|说明|类型|
|---|---|---|---|
|**Header**|**appId**  <br>*必填*|appId|string|
|**Header**|**timestamp**  <br>*必填*|timestamp|string|
|**Header**|**x-userinfo**  <br>*可选*|用户信息|string|
|**Body**|**orderVO**  <br>*必填*|orderVO|[LogistOrderVo](#logistordervo)|


#### 响应

|HTTP代码|说明|类型|
|---|---|---|
|**200**|OK|[Resp](#resp)|
|**201**|Created|无内容|
|**401**|Unauthorized|无内容|
|**403**|Forbidden|无内容|
|**404**|Not Found|无内容|


#### 消耗

* `application/json`


#### 生成

* `\*/*`


#### 标签

* logist-controller


<a name="addeorderusingpost"></a>
### 电子面单下单
```
POST /{tenantId}/enterprise/v1/logistics/eorder
```


#### 说明
返回单号和打印面单模板


#### 参数

|类型|名称|说明|类型|
|---|---|---|---|
|**Header**|**x-userinfo**  <br>*可选*|用户信息|string|
|**Path**|**tenantId**  <br>*必填*|租户id|string|
|**Query**|**appId**  <br>*必填*|应用id|string|
|**Query**|**companyId**  <br>*必填*|公司id|string|
|**Body**|**orderVO**  <br>*必填*|orderVO|[OrderReq](#orderreq)|


#### 响应

|HTTP代码|说明|类型|
|---|---|---|
|**200**|OK|[DefaultResponse«OrderResponse»](#c692c8c94d40ab9aa68fe2a6090dbc6d)|
|**201**|Created|无内容|
|**401**|Unauthorized|无内容|
|**403**|Forbidden|无内容|
|**404**|Not Found|无内容|


#### 消耗

* `application/json`


#### 生成

* `\*/*`


#### 标签

* logistics


<a name="queryexpresscompanyusingget"></a>
### 查询快递公司
```
GET /{tenantId}/enterprise/v1/logistics/express/company
```


#### 说明
返回快递公司信息


#### 参数

|类型|名称|说明|类型|
|---|---|---|---|
|**Header**|**x-userinfo**  <br>*可选*|用户信息|string|
|**Path**|**tenantId**  <br>*必填*|租户id|string|
|**Query**|**appId**  <br>*必填*|应用id|string|
|**Query**|**companyId**  <br>*必填*|公司id|string|


#### 响应

|HTTP代码|说明|类型|
|---|---|---|
|**200**|OK|[DefaultResponse«List«ExpressCompanyResponse»»](#249bb6346ef6fd2e23b8c46d0d9d5e4f)|
|**401**|Unauthorized|无内容|
|**403**|Forbidden|无内容|
|**404**|Not Found|无内容|


#### 生成

* `application/json;charset=UTF-8`


#### 标签

* logistics


<a name="addbookingorderusingpost"></a>
### 预约取件
```
POST /{tenantId}/enterprise/v1/logistics/order
```


#### 说明
下单成功后，快递员按预约时间上门取件


#### 参数

|类型|名称|说明|类型|
|---|---|---|---|
|**Header**|**x-userinfo**  <br>*可选*|用户信息|string|
|**Path**|**tenantId**  <br>*必填*|租户id|string|
|**Query**|**appId**  <br>*必填*|应用id|string|
|**Query**|**companyId**  <br>*必填*|公司id|string|
|**Body**|**orderVO**  <br>*必填*|orderVO|[OrderBookingReq](#orderbookingreq)|


#### 响应

|HTTP代码|说明|类型|
|---|---|---|
|**200**|OK|[DefaultResponse«OrderBookingResponse»](#04eb2a960d526c7e2d84dadbce8d40e0)|
|**201**|Created|无内容|
|**401**|Unauthorized|无内容|
|**403**|Forbidden|无内容|
|**404**|Not Found|无内容|


#### 消耗

* `application/json`


#### 生成

* `\*/*`


#### 标签

* logistics


<a name="trackcallbackusingpost"></a>
### 物流信息回调服务
```
POST /{tenantId}/enterprise/v1/logistics/order/callback
```


#### 说明
供快递鸟API调用；接收到信息后，会把消息放在queue里，然后再去消费该队列，更新订单的物流信息


#### 参数

|类型|名称|说明|类型|
|---|---|---|---|
|**Header**|**x-userinfo**  <br>*可选*|用户信息|string|
|**Path**|**tenantId**  <br>*必填*|tenantId|string|
|**Body**|**trackReq**  <br>*必填*|trackReq|[TrackCallBackReq](#trackcallbackreq)|


#### 响应

|HTTP代码|说明|类型|
|---|---|---|
|**200**|OK|[DefaultResponse](#defaultresponse)|
|**201**|Created|无内容|
|**401**|Unauthorized|无内容|
|**403**|Forbidden|无内容|
|**404**|Not Found|无内容|


#### 消耗

* `application/json`


#### 生成

* `\*/*`


#### 标签

* logistics


<a name="querytrackusingget"></a>
### 查询轨迹
```
GET /{tenantId}/enterprise/v1/logistics/order/track
```


#### 说明
返回订单轨迹信息


#### 参数

|类型|名称|说明|类型|
|---|---|---|---|
|**Header**|**x-userinfo**  <br>*可选*|用户信息|string|
|**Path**|**tenantId**  <br>*必填*|租户id|string|
|**Query**|**appId**  <br>*必填*|应用id|string|
|**Query**|**companyId**  <br>*必填*|公司id|string|
|**Query**|**logisticCode**  <br>*可选*|快递单号|string|
|**Query**|**orderCode**  <br>*可选*|订单编号|string|


#### 响应

|HTTP代码|说明|类型|
|---|---|---|
|**200**|OK|[DefaultResponse«TrackResponse»](#93c9a20a33fc85973d865377553efe17)|
|**401**|Unauthorized|无内容|
|**403**|Forbidden|无内容|
|**404**|Not Found|无内容|


#### 生成

* `\*/*`


#### 标签

* logistics


<a name="ordersubscribeusingpost"></a>
### 订阅轨迹
```
POST /{tenantId}/enterprise/v1/logistics/order/track/subscription
```


#### 参数

|类型|名称|说明|类型|
|---|---|---|---|
|**Header**|**x-userinfo**  <br>*可选*|用户信息|string|
|**Path**|**tenantId**  <br>*必填*|租户id|string|
|**Query**|**appId**  <br>*必填*|应用id|string|
|**Query**|**companyId**  <br>*必填*|公司id|string|
|**Body**|**orderVO**  <br>*必填*|orderVO|[OrderSubscribeReq](#ordersubscribereq)|


#### 响应

|HTTP代码|说明|类型|
|---|---|---|
|**200**|OK|[DefaultResponse«TrackSubscriptionResp»](#1d537d7ee2fb5f0a9a52ae62fc2addf1)|
|**201**|Created|无内容|
|**401**|Unauthorized|无内容|
|**403**|Forbidden|无内容|
|**404**|Not Found|无内容|


#### 消耗

* `application/json`


#### 生成

* `\*/*`


#### 标签

* logistics




<a name="definitions"></a>
## 定义

<a name="defaultresponse"></a>
### DefaultResponse

|名称|说明|类型|
|---|---|---|
|**code**  <br>*可选*|状态码  <br>**样例** : `"LGSTZZ0200"`|string|
|**message**  <br>*可选*|状态描述  <br>**样例** : `"请求成功"`|string|
|**result**  <br>*可选*|返回数据|object|


<a name="249bb6346ef6fd2e23b8c46d0d9d5e4f"></a>
### DefaultResponse«List«ExpressCompanyResponse»»

|名称|说明|类型|
|---|---|---|
|**code**  <br>*可选*|状态码  <br>**样例** : `"LGSTZZ0200"`|string|
|**message**  <br>*可选*|状态描述  <br>**样例** : `"请求成功"`|string|
|**result**  <br>*可选*|返回数据|< [ExpressCompanyResponse](#expresscompanyresponse) > array|


<a name="04eb2a960d526c7e2d84dadbce8d40e0"></a>
### DefaultResponse«OrderBookingResponse»

|名称|说明|类型|
|---|---|---|
|**code**  <br>*可选*|状态码  <br>**样例** : `"LGSTZZ0200"`|string|
|**message**  <br>*可选*|状态描述  <br>**样例** : `"请求成功"`|string|
|**result**  <br>*可选*|返回数据|[OrderBookingResponse](#orderbookingresponse)|


<a name="c692c8c94d40ab9aa68fe2a6090dbc6d"></a>
### DefaultResponse«OrderResponse»

|名称|说明|类型|
|---|---|---|
|**code**  <br>*可选*|状态码  <br>**样例** : `"LGSTZZ0200"`|string|
|**message**  <br>*可选*|状态描述  <br>**样例** : `"请求成功"`|string|
|**result**  <br>*可选*|返回数据|[OrderResponse](#orderresponse)|


<a name="93c9a20a33fc85973d865377553efe17"></a>
### DefaultResponse«TrackResponse»

|名称|说明|类型|
|---|---|---|
|**code**  <br>*可选*|状态码  <br>**样例** : `"LGSTZZ0200"`|string|
|**message**  <br>*可选*|状态描述  <br>**样例** : `"请求成功"`|string|
|**result**  <br>*可选*|返回数据|[TrackResponse](#trackresponse)|


<a name="1d537d7ee2fb5f0a9a52ae62fc2addf1"></a>
### DefaultResponse«TrackSubscriptionResp»

|名称|说明|类型|
|---|---|---|
|**code**  <br>*可选*|状态码  <br>**样例** : `"LGSTZZ0200"`|string|
|**message**  <br>*可选*|状态描述  <br>**样例** : `"请求成功"`|string|
|**result**  <br>*可选*|返回数据|[TrackSubscriptionResp](#tracksubscriptionresp)|


<a name="expresscompanyresponse"></a>
### ExpressCompanyResponse
快递公司


|名称|说明|类型|
|---|---|---|
|**eorderable**  <br>*可选*|支持电子面单  <br>**样例** : `false`|boolean|
|**expressCode**  <br>*可选*|快递公司编码  <br>**样例** : `"SF"`|string|
|**expressName**  <br>*可选*|快递公司名称  <br>**样例** : `"顺丰速运"`|string|
|**orderable**  <br>*可选*|支持预约取件  <br>**样例** : `false`|boolean|
|**trackable**  <br>*可选*|支持轨迹查询  <br>**样例** : `false`|boolean|


<a name="logistordervo"></a>
### LogistOrderVo

|名称|类型|
|---|---|
|**appid**  <br>*可选*|string|
|**companyId**  <br>*可选*|string|
|**customerId**  <br>*可选*|string|
|**customerName**  <br>*可选*|string|
|**expressCode**  <br>*可选*|string|
|**expressName**  <br>*可选*|string|
|**expressType**  <br>*可选*|string|
|**flieType**  <br>*可选*|string|
|**orderNo**  <br>*可选*|string|
|**receiveAddress**  <br>*可选*|string|
|**receiveCity**  <br>*可选*|string|
|**receiveCounty**  <br>*可选*|string|
|**receiveName**  <br>*可选*|string|
|**receivePostalCode**  <br>*可选*|string|
|**receiveProvince**  <br>*可选*|string|
|**receiveTel**  <br>*可选*|string|
|**remark**  <br>*可选*|string|
|**sendStartTime**  <br>*可选*|string|
|**senderAddress**  <br>*可选*|string|
|**senderCity**  <br>*可选*|string|
|**senderCounty**  <br>*可选*|string|
|**senderName**  <br>*可选*|string|
|**senderPostalCode**  <br>*可选*|string|
|**senderProvince**  <br>*可选*|string|
|**senderTel**  <br>*可选*|string|
|**tenantId**  <br>*可选*|string|


<a name="orderbookingreq"></a>
### OrderBookingReq
预约取件请求


|名称|说明|类型|
|---|---|---|
|**collectEndTime**  <br>*可选*|揽件结束时间(yyyy-MM-dd HH:mm:ss)  <br>**样例** : `"2019-09-26 19:18:07"`|string (date-time)|
|**collectStartTime**  <br>*可选*|揽件开始时间(yyyy-MM-dd HH:mm:ss)  <br>**样例** : `"2019-09-26 15:18:07"`|string (date-time)|
|**expressCode**  <br>*必填*|快递公司编码  <br>**样例** : `"SF"`|string|
|**goodsName**  <br>*可选*|商品名称  <br>**样例** : `"发票"`|string|
|**monthCode**  <br>*可选*|月结卡号(payType=3 时必填)  <br>**样例** : `"SF8866998"`|string|
|**orderCode**  <br>*必填*|订单编号  <br>**样例** : `"201909050001"`|string|
|**payType**  <br>*必填*|运费支付方式(1.现付 2.到付 3.月结)  <br>**样例** : `1`|integer (int32)|
|**quantity**  <br>*可选*|数量  <br>**样例** : `1`|integer (int32)|
|**receiverAddress**  <br>*必填*|收件详细地址  <br>**样例** : `"商都路188号101室"`|string|
|**receiverCity**  <br>*必填*|收件市  <br>**样例** : `"郑州市"`|string|
|**receiverDistrict**  <br>*必填*|收件区/县  <br>**样例** : `"金水区"`|string|
|**receiverName**  <br>*必填*|收件人姓名  <br>**样例** : `"李小勇"`|string|
|**receiverPostCode**  <br>*可选*|收件人邮编(ShipperCode 为EMS、YZPY、YZBK 时必填)  <br>**样例** : `"450003"`|string|
|**receiverProvince**  <br>*必填*|收件省  <br>**样例** : `"河南省"`|string|
|**receiverTel**  <br>*必填*|收件人电话  <br>**样例** : `"13774392605"`|string|
|**remark**  <br>*可选*|备注|string|
|**senderAddress**  <br>*必填*|发件详细地址  <br>**样例** : `"富南路199弄101室"`|string|
|**senderCity**  <br>*必填*|发件市  <br>**样例** : `"上海市"`|string|
|**senderDistrict**  <br>*必填*|发件区/县  <br>**样例** : `"宝山区"`|string|
|**senderName**  <br>*必填*|发件人姓名  <br>**样例** : `"王大强"`|string|
|**senderPostCode**  <br>*可选*|发件人邮编(ShipperCode 为EMS、YZPY、YZBK 时必填)  <br>**样例** : `"201908"`|string|
|**senderProvince**  <br>*必填*|发件省  <br>**样例** : `"上海"`|string|
|**senderTel**  <br>*必填*|发件人电话  <br>**样例** : `"13512345678"`|string|
|**volume**  <br>*可选*|体积  <br>**样例** : `0`|integer (int32)|


<a name="orderbookingresponse"></a>
### OrderBookingResponse
预约下单返回


|名称|说明|类型|
|---|---|---|
|**expressCode**  <br>*可选*|快递公司编码  <br>**样例** : `"SF"`|string|
|**logisticCode**  <br>*可选*|快递单号  <br>**样例** : `"SF1011327874518"`|string|
|**orderCode**  <br>*可选*|订单编号  <br>**样例** : `"PYT2019090800001"`|string|


<a name="orderreq"></a>
### OrderReq
电子面单请求


|名称|说明|类型|
|---|---|---|
|**collectEndTime**  <br>*可选*|揽件结束时间(yyyy-MM-dd HH:mm:ss)  <br>**样例** : `"2019-09-26 19:18:07"`|string (date-time)|
|**collectStartTime**  <br>*可选*|揽件开始时间(yyyy-MM-dd HH:mm:ss)  <br>**样例** : `"2019-09-26 15:18:07"`|string (date-time)|
|**customerName**  <br>*可选*|电子面单客户号|string|
|**customerPwd**  <br>*可选*|电子面单客户密钥|string|
|**expressCode**  <br>*必填*|快递公司编码  <br>**样例** : `"SF"`|string|
|**goodsName**  <br>*可选*|商品名称  <br>**样例** : `"发票"`|string|
|**monthCode**  <br>*可选*|月结卡号(payType=3 时必填)  <br>**样例** : `"SF8866998"`|string|
|**orderCode**  <br>*必填*|订单编号  <br>**样例** : `"201909050001"`|string|
|**payType**  <br>*必填*|运费支付方式(1.现付 2.到付 3.月结)  <br>**样例** : `1`|integer (int32)|
|**quantity**  <br>*可选*|数量  <br>**样例** : `1`|integer (int32)|
|**receiverAddress**  <br>*必填*|收件详细地址  <br>**样例** : `"商都路188号101室"`|string|
|**receiverCity**  <br>*必填*|收件市  <br>**样例** : `"郑州市"`|string|
|**receiverDistrict**  <br>*必填*|收件区/县  <br>**样例** : `"金水区"`|string|
|**receiverName**  <br>*必填*|收件人姓名  <br>**样例** : `"李小勇"`|string|
|**receiverPostCode**  <br>*可选*|收件人邮编(ShipperCode 为EMS、YZPY、YZBK 时必填)  <br>**样例** : `"450003"`|string|
|**receiverProvince**  <br>*必填*|收件省  <br>**样例** : `"河南省"`|string|
|**receiverTel**  <br>*必填*|收件人电话  <br>**样例** : `"13774392605"`|string|
|**remark**  <br>*可选*|备注|string|
|**sendSite**  <br>*可选*|所属网点|string|
|**sendStaff**  <br>*可选*|收件快递员|string|
|**senderAddress**  <br>*必填*|发件详细地址  <br>**样例** : `"富南路199弄101室"`|string|
|**senderCity**  <br>*必填*|发件市  <br>**样例** : `"上海市"`|string|
|**senderDistrict**  <br>*必填*|发件区/县  <br>**样例** : `"宝山区"`|string|
|**senderName**  <br>*必填*|发件人姓名  <br>**样例** : `"王大强"`|string|
|**senderPostCode**  <br>*可选*|发件人邮编(ShipperCode 为EMS、YZPY、YZBK 时必填)  <br>**样例** : `"201908"`|string|
|**senderProvince**  <br>*必填*|发件省  <br>**样例** : `"上海"`|string|
|**senderTel**  <br>*必填*|发件人电话  <br>**样例** : `"13512345678"`|string|
|**templateSize**  <br>*可选*|面单模板尺寸(不传为默认模板)|string|
|**volume**  <br>*可选*|体积  <br>**样例** : `0`|integer (int32)|


<a name="orderresponse"></a>
### OrderResponse
电子面单下单返回


|名称|说明|类型|
|---|---|---|
|**estimatedDeliveryTime**  <br>*可选*|订单预计到货时间yyyy-mm-dd  <br>**样例** : `"2019-09-10"`|string (date-time)|
|**expressCode**  <br>*可选*|快递公司编码  <br>**样例** : `"SF"`|string|
|**logisticCode**  <br>*可选*|快递单号  <br>**样例** : `"SF1011327874518"`|string|
|**orderCode**  <br>*可选*|订单编号  <br>**样例** : `"PYT2019090800001"`|string|
|**printTemplate**  <br>*可选*|面单打印模板内容(html格式)|string|


<a name="ordersubscribereq"></a>
### OrderSubscribeReq
订阅请求


|名称|说明|类型|
|---|---|---|
|**collectEndTime**  <br>*可选*|揽件结束时间(yyyy-MM-dd HH:mm:ss)  <br>**样例** : `"2019-09-26 19:18:07"`|string (date-time)|
|**collectStartTime**  <br>*可选*|揽件开始时间(yyyy-MM-dd HH:mm:ss)  <br>**样例** : `"2019-09-26 15:18:07"`|string (date-time)|
|**expressCode**  <br>*必填*|快递公司编码  <br>**样例** : `"SF"`|string|
|**goodsName**  <br>*可选*|商品名称  <br>**样例** : `"发票"`|string|
|**logisticCode**  <br>*必填*|快递单号  <br>**样例** : `"SF7444400619915"`|string|
|**monthCode**  <br>*可选*|月结卡号(payType=3 时必填)  <br>**样例** : `"SF8866998"`|string|
|**orderCode**  <br>*必填*|订单编号  <br>**样例** : `"201909050001"`|string|
|**payType**  <br>*必填*|运费支付方式(1.现付 2.到付 3.月结)  <br>**样例** : `1`|integer (int32)|
|**quantity**  <br>*可选*|数量  <br>**样例** : `1`|integer (int32)|
|**receiverAddress**  <br>*必填*|收件详细地址  <br>**样例** : `"商都路188号101室"`|string|
|**receiverCity**  <br>*必填*|收件市  <br>**样例** : `"郑州市"`|string|
|**receiverDistrict**  <br>*必填*|收件区/县  <br>**样例** : `"金水区"`|string|
|**receiverName**  <br>*必填*|收件人姓名  <br>**样例** : `"李小勇"`|string|
|**receiverPostCode**  <br>*可选*|收件人邮编(ShipperCode 为EMS、YZPY、YZBK 时必填)  <br>**样例** : `"450003"`|string|
|**receiverProvince**  <br>*必填*|收件省  <br>**样例** : `"河南省"`|string|
|**receiverTel**  <br>*必填*|收件人电话  <br>**样例** : `"13774392605"`|string|
|**remark**  <br>*可选*|备注|string|
|**senderAddress**  <br>*必填*|发件详细地址  <br>**样例** : `"富南路199弄101室"`|string|
|**senderCity**  <br>*必填*|发件市  <br>**样例** : `"上海市"`|string|
|**senderDistrict**  <br>*必填*|发件区/县  <br>**样例** : `"宝山区"`|string|
|**senderName**  <br>*必填*|发件人姓名  <br>**样例** : `"王大强"`|string|
|**senderPostCode**  <br>*可选*|发件人邮编(ShipperCode 为EMS、YZPY、YZBK 时必填)  <br>**样例** : `"201908"`|string|
|**senderProvince**  <br>*必填*|发件省  <br>**样例** : `"上海"`|string|
|**senderTel**  <br>*必填*|发件人电话  <br>**样例** : `"13512345678"`|string|
|**volume**  <br>*可选*|体积  <br>**样例** : `0`|integer (int32)|


<a name="resp"></a>
### Resp

|名称|类型|
|---|---|
|**respCode**  <br>*可选*|string|
|**respMsg**  <br>*可选*|string|
|**respName**  <br>*可选*|string|
|**value**  <br>*可选*|object|


<a name="trackcallbackreq"></a>
### TrackCallBackReq

|名称|类型|
|---|---|
|**code**  <br>*可选*|string|
|**message**  <br>*可选*|string|
|**result**  <br>*可选*|object|


<a name="trackresponse"></a>
### TrackResponse
物流轨迹返回


|名称|说明|类型|
|---|---|---|
|**expressCode**  <br>*可选*|快递公司编码  <br>**样例** : `"SF"`|string|
|**logisticCode**  <br>*可选*|快递单号  <br>**样例** : `"SF1011327874518"`|string|
|**orderCode**  <br>*可选*|订单编号  <br>**样例** : `"PYT2019090800001"`|string|
|**traces**  <br>*可选*|物流信息|< [TrackVO](#trackvo) > array|


<a name="tracksubscriptionresp"></a>
### TrackSubscriptionResp
轨迹订阅返回


|名称|说明|类型|
|---|---|---|
|**estimatedDeliveryTime**  <br>*可选*|订单预计到货时间yyyy-mm-dd  <br>**样例** : `"2019-09-12"`|string (date-time)|
|**updateTime**  <br>*可选*|更新时间  <br>**样例** : `"2019-09-10 10:20:30"`|string (date-time)|


<a name="trackvo"></a>
### TrackVO
物流轨迹


|名称|说明|类型|
|---|---|---|
|**acceptStation**  <br>*必填*|接收信息  <br>**样例** : `"【宝山站】的【票易通】已收件"`|string|
|**acceptTime**  <br>*必填*|接收时间  <br>**样例** : `"2018-10-26 18:31:38"`|string (date-time)|
|**remark**  <br>*可选*|备注|string|





