# 电子合同接口样式


<a name="overview"></a>
## 概览
Author: Kenny Wong


### 版本信息
*版本* : 1.0.0


### URI scheme
*域名* : econtract-fat.phoenix-t.xforceplus.com  
*基础路径* : /


### 标签

* electronic contract : Contract Controller
* electronic seal : Seal Controller




<a name="paths"></a>
## 路径

<a name="createcontractusingpost"></a>
### 创建合同
```
POST /{tenantId}/enterprise/v1/econtract/contracts
```


#### 参数

|类型|名称|说明|类型|
|---|---|---|---|
|**Header**|**x-userinfo**  <br>*可选*|用户信息|string|
|**Path**|**tenantId**  <br>*必填*|租户id|integer (int64)|
|**Query**|**appId**  <br>*必填*|应用id|integer (int64)|
|**Query**|**companyId**  <br>*必填*|公司id|integer (int64)|
|**Body**|**contractCreationRequest**  <br>*必填*|创建合同请求|[ContractCreationRequest](#contractcreationrequest)|


#### 响应

|HTTP代码|说明|类型|
|---|---|---|
|**200**|OK|[DefaultResponse](#defaultresponse)|
|**201**|Created|无内容|
|**401**|Unauthorized|无内容|
|**403**|Forbidden|无内容|
|**404**|Not Found|无内容|


#### 消耗

* `application/json;charset=UTF-8`


#### 生成

* `application/json;charset=UTF-8`


#### 标签

* electronic contract


<a name="uploadtemplateusingpost"></a>
### 上传合同模板
```
POST /{tenantId}/enterprise/v1/econtract/contracts/templates
```


#### 参数

|类型|名称|说明|类型|
|---|---|---|---|
|**Header**|**x-userinfo**  <br>*可选*|用户信息|string|
|**Path**|**tenantId**  <br>*必填*|租户id|integer (int64)|
|**Query**|**appId**  <br>*必填*|应用id|integer (int64)|
|**Query**|**companyId**  <br>*必填*|公司id|integer (int64)|
|**FormData**|**multipartFile**  <br>*必填*|合同模板文件|file|


#### 响应

|HTTP代码|说明|类型|
|---|---|---|
|**200**|OK|[DefaultResponse](#defaultresponse)|
|**201**|Created|无内容|
|**401**|Unauthorized|无内容|
|**403**|Forbidden|无内容|
|**404**|Not Found|无内容|


#### 消耗

* `multipart/form-data`


#### 生成

* `application/json;charset=UTF-8`


#### 标签

* electronic contract


<a name="obtaincontractusingget"></a>
### 获取合同
```
GET /{tenantId}/enterprise/v1/econtract/contracts/{contractId}
```


#### 参数

|类型|名称|说明|类型|
|---|---|---|---|
|**Header**|**x-userinfo**  <br>*可选*|用户信息|string|
|**Path**|**contractId**  <br>*必填*|合同id|string|
|**Path**|**tenantId**  <br>*必填*|租户id|integer (int64)|
|**Query**|**appId**  <br>*必填*|应用id|integer (int64)|
|**Query**|**companyId**  <br>*必填*|公司id|integer (int64)|
|**Query**|**download**  <br>*必填*|是否需要下载|boolean|


#### 响应

|HTTP代码|说明|类型|
|---|---|---|
|**200**|OK|[DefaultResponse](#defaultresponse)|
|**401**|Unauthorized|无内容|
|**403**|Forbidden|无内容|
|**404**|Not Found|无内容|


#### 生成

* `application/json;charset=UTF-8`


#### 标签

* electronic contract


<a name="signcontractusingpost"></a>
### 签署合同
```
POST /{tenantId}/enterprise/v1/econtract/contracts/{contractId}/signature
```


#### 参数

|类型|名称|说明|类型|
|---|---|---|---|
|**Header**|**x-userinfo**  <br>*可选*|用户信息|string|
|**Path**|**contractId**  <br>*必填*|合同id|string|
|**Path**|**tenantId**  <br>*必填*|租户id|integer (int64)|
|**Query**|**appId**  <br>*必填*|应用id|integer (int64)|
|**Query**|**auto**  <br>*必填*|是否自动签署|boolean|
|**Query**|**companyId**  <br>*必填*|公司id|integer (int64)|
|**Body**|**contractSignRequest**  <br>*必填*|签署合同请求|[ContractSignRequest](#contractsignrequest)|


#### 响应

|HTTP代码|说明|类型|
|---|---|---|
|**200**|OK|[DefaultResponse](#defaultresponse)|
|**201**|Created|无内容|
|**401**|Unauthorized|无内容|
|**403**|Forbidden|无内容|
|**404**|Not Found|无内容|


#### 消耗

* `application/json;charset=UTF-8`


#### 生成

* `application/json;charset=UTF-8`


#### 标签

* electronic contract


<a name="uploadsealusingpost"></a>
### 上传签章文字或图片
```
POST /{tenantId}/enterprise/v1/econtract/seals
```


#### 参数

|类型|名称|说明|类型|
|---|---|---|---|
|**Header**|**x-userinfo**  <br>*可选*|用户信息|string|
|**Path**|**tenantId**  <br>*必填*|租户id|integer (int64)|
|**Query**|**appId**  <br>*必填*|应用id|integer (int64)|
|**Query**|**companyId**  <br>*必填*|公司id|integer (int64)|
|**Body**|**sealUploadRequest**  <br>*必填*|签章上传请求|[SealUploadRequest](#sealuploadrequest)|


#### 响应

|HTTP代码|说明|类型|
|---|---|---|
|**200**|OK|[DefaultResponse](#defaultresponse)|
|**201**|Created|无内容|
|**401**|Unauthorized|无内容|
|**403**|Forbidden|无内容|
|**404**|Not Found|无内容|


#### 消耗

* `application/json;charset=UTF-8`


#### 生成

* `application/json;charset=UTF-8`


#### 标签

* electronic seal




<a name="definitions"></a>
## 定义

<a name="contractcreationrequest"></a>
### ContractCreationRequest

|名称|说明|类型|
|---|---|---|
|**contractTitle**  <br>*可选*|合同标题  <br>**样例** : `"XX投资合同"`|string|
|**dynamicTables**  <br>*可选*|动态表格|< string > array|
|**fontSize**  <br>*可选*|字体大小，参考word字体设置，例如：10,12.5,14  <br>**样例** : `"10"`|string|
|**fontType**  <br>*可选*|字体类型 0-宋体 1-仿宋 2-黑体 3-楷体 4-微软雅黑  <br>**样例** : `"0"`|string|
|**parameterMap**  <br>*可选*|合同参数|object|
|**templateId**  <br>*可选*|合同模板id  <br>**样例** : `"123456"`|string|


<a name="contractsignrequest"></a>
### ContractSignRequest

|名称|说明|类型|
|---|---|---|
|**contractTitle**  <br>*可选*|合同标题  <br>**样例** : `"XX投资合同"`|string|
|**parameters**  <br>*可选*|自动签署可选参数|object|
|**sealId**  <br>*可选*|签章id，通过上传签章图片返回，注意上传签章文字不返回签章id）  <br>**样例** : `"123456"`|string|
|**transactionId**  <br>*可选*|自动签署事务id  <br>**样例** : `"123456"`|string|


<a name="defaultresponse"></a>
### DefaultResponse

|名称|说明|类型|
|---|---|---|
|**code**  <br>*可选*|状态码  <br>**样例** : `"ELCCZZ0200"`|string|
|**message**  <br>*可选*|状态描述  <br>**样例** : `"请求成功"`|string|
|**result**  <br>*可选*|返回数据|object|


<a name="sealuploadrequest"></a>
### SealUploadRequest

|名称|说明|类型|
|---|---|---|
|**sealBody**  <br>*可选*|签章文字内容（当sealBody非空时，sealImageBase64必须为空）  <br>**样例** : `"XXX公司"`|string|
|**sealImageBase64**  <br>*可选*|基于base64编码的电子签章图片（当sealImageBase64非空时，sealBody必须为空）  <br>**样例** : `"123456"`|string|





