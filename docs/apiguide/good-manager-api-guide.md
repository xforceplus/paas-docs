# 商品管理服务接口样式


<a name="overview"></a>
## 概览

### 版本信息
*版本* : 1.0.0


### URI scheme
*域名* : goods-manger-fat.phoenix-t.xforceplus.com  
*基础路径* : /


### 标签

* goods-controller : Goods Controller
* goods-type-controller : Goods Type Controller
* tax-code-controller : Tax Code Controller
* tax-number-controller : Tax Number Controller




<a name="paths"></a>
## 路径

<a name="creategoodsusingpost"></a>
### 新增商品
```
POST /{tenantId}/enterprise/v1/goods
```


#### 参数

|类型|名称|说明|类型|
|---|---|---|---|
|**Path**|**tenantId**  <br>*可选*|租户id|integer (int64)|
|**Query**|**appId**  <br>*可选*|产品线id|integer (int64)|
|**Body**|**createGoodsParam**  <br>*必填*|商品信息|[CreateGoodsParam](#creategoodsparam)|


#### 响应

|HTTP代码|说明|类型|
|---|---|---|
|**200**|OK|[BaseResponse«string»](#c2b8bd5459ac78f2e4e0011198c1a1d4)|
|**201**|Created|无内容|
|**401**|Unauthorized|无内容|
|**403**|Forbidden|无内容|
|**404**|Not Found|无内容|


#### 消耗

* `application/json`


#### 生成

* `\*/*`


#### 标签

* goods-controller


<a name="querygoodsusingget"></a>
### 查询商品信息
```
GET /{tenantId}/enterprise/v1/goods
```


#### 参数

|类型|名称|说明|类型|
|---|---|---|---|
|**Path**|**tenantId**  <br>*可选*|租户id|integer (int64)|
|**Query**|**appId**  <br>*必填*|产品线id|integer (int64)|
|**Query**|**companyName**  <br>*可选*|公司名称|string|
|**Query**|**goodsName**  <br>*可选*|商品名称|string|
|**Query**|**pageNo**  <br>*必填*|页码|integer (int32)|
|**Query**|**pageSize**  <br>*必填*|每页数量|integer (int32)|
|**Query**|**typeCode**  <br>*必填*|商品类型code|string|


#### 响应

|HTTP代码|说明|类型|
|---|---|---|
|**200**|OK|[BaseResponse«GoodsPage»](#6320a621975b3f52a1bae3b3ba4cede5)|
|**401**|Unauthorized|无内容|
|**403**|Forbidden|无内容|
|**404**|Not Found|无内容|


#### 生成

* `\*/*`


#### 标签

* goods-controller


<a name="creategoodstypeinfousingpost"></a>
### 新增商品类型
```
POST /{tenantId}/enterprise/v1/goods-type
```


#### 参数

|类型|名称|说明|类型|
|---|---|---|---|
|**Path**|**tenantId**  <br>*可选*|租户id|integer (int64)|
|**Body**|**createGoodsTypeParam**  <br>*必填*|商品类型|[CreateGoodsTypeParam](#creategoodstypeparam)|


#### 响应

|HTTP代码|说明|类型|
|---|---|---|
|**200**|OK|[BaseResponse«string»](#c2b8bd5459ac78f2e4e0011198c1a1d4)|
|**201**|Created|无内容|
|**401**|Unauthorized|无内容|
|**403**|Forbidden|无内容|
|**404**|Not Found|无内容|


#### 消耗

* `application/json`


#### 生成

* `\*/*`


#### 标签

* goods-type-controller


<a name="deletegoodstypeinfousingdelete"></a>
### 删除商品类型
```
DELETE /{tenantId}/enterprise/v1/goods-type/{id}
```


#### 参数

|类型|名称|说明|类型|
|---|---|---|---|
|**Path**|**id**  <br>*必填*|商品类型Id|integer (int64)|
|**Path**|**tenantId**  <br>*可选*|租户id|integer (int64)|


#### 响应

|HTTP代码|说明|类型|
|---|---|---|
|**200**|OK|[BaseResponse«string»](#c2b8bd5459ac78f2e4e0011198c1a1d4)|
|**204**|No Content|无内容|
|**401**|Unauthorized|无内容|
|**403**|Forbidden|无内容|


#### 生成

* `\*/*`


#### 标签

* goods-type-controller


<a name="creategoodsmappingrelationusingpost"></a>
### 新增商品映射关系
```
POST /{tenantId}/enterprise/v1/goods/relations
```


#### 参数

|类型|名称|说明|类型|
|---|---|---|---|
|**Path**|**tenantId**  <br>*必填*|租户id|integer (int64)|
|**Query**|**appId**  <br>*必填*|产品线id|integer (int64)|
|**Body**|**relationParams**  <br>*必填*|商品信息|[RelationParams](#relationparams)|


#### 响应

|HTTP代码|说明|类型|
|---|---|---|
|**200**|OK|[BaseResponse«string»](#c2b8bd5459ac78f2e4e0011198c1a1d4)|
|**201**|Created|无内容|
|**401**|Unauthorized|无内容|
|**403**|Forbidden|无内容|
|**404**|Not Found|无内容|


#### 消耗

* `application/json`


#### 生成

* `\*/*`


#### 标签

* goods-controller


<a name="deletegoodsrelationusingdelete"></a>
### 删除商品映射关系
```
DELETE /{tenantId}/enterprise/v1/goods/relations/{id}
```


#### 参数

|类型|名称|说明|类型|
|---|---|---|---|
|**Path**|**id**  <br>*必填*|商品id|integer (int64)|
|**Path**|**tenantId**  <br>*必填*|租户id|integer (int64)|
|**Query**|**appId**  <br>*必填*|产品线id|integer (int64)|


#### 响应

|HTTP代码|说明|类型|
|---|---|---|
|**200**|OK|[BaseResponse«string»](#c2b8bd5459ac78f2e4e0011198c1a1d4)|
|**204**|No Content|无内容|
|**401**|Unauthorized|无内容|
|**403**|Forbidden|无内容|


#### 生成

* `\*/*`


#### 标签

* goods-controller


<a name="querygoodsdetailusingget"></a>
### 查询商品信息详情
```
GET /{tenantId}/enterprise/v1/goods/{goodsNo}
```


#### 参数

|类型|名称|说明|类型|
|---|---|---|---|
|**Path**|**goodsNo**  <br>*可选*|商品编码|string|
|**Path**|**tenantId**  <br>*必填*|租户id|integer (int64)|
|**Query**|**appId**  <br>*必填*|产品线id|integer (int64)|
|**Query**|**goodsTypeCode**  <br>*必填*|商品类型code|string|
|**Query**|**providerTenantId**  <br>*可选*|供应商租户id|integer (int64)|


#### 响应

|HTTP代码|说明|类型|
|---|---|---|
|**200**|OK|[BaseResponse«GoodsDetail»](#746617118ea1b1a50eb86f6057507377)|
|**401**|Unauthorized|无内容|
|**403**|Forbidden|无内容|
|**404**|Not Found|无内容|


#### 生成

* `\*/*`


#### 标签

* goods-controller


<a name="updategoodsusingput"></a>
### 修改商品信息
```
PUT /{tenantId}/enterprise/v1/goods/{id}
```


#### 参数

|类型|名称|说明|类型|
|---|---|---|---|
|**Path**|**id**  <br>*必填*|商品id|integer (int64)|
|**Path**|**tenantId**  <br>*必填*|租户id|integer (int64)|
|**Query**|**appId**  <br>*可选*|产品线id|integer (int64)|
|**Body**|**goods**  <br>*必填*|商品信息|[Goods](#goods)|


#### 响应

|HTTP代码|说明|类型|
|---|---|---|
|**200**|OK|[BaseResponse«string»](#c2b8bd5459ac78f2e4e0011198c1a1d4)|
|**201**|Created|无内容|
|**401**|Unauthorized|无内容|
|**403**|Forbidden|无内容|
|**404**|Not Found|无内容|


#### 消耗

* `application/json`


#### 生成

* `\*/*`


#### 标签

* goods-controller


<a name="deletegoodsusingdelete"></a>
### 删除商品信息
```
DELETE /{tenantId}/enterprise/v1/goods/{id}
```


#### 参数

|类型|名称|说明|类型|
|---|---|---|---|
|**Path**|**id**  <br>*必填*|商品id|integer (int64)|
|**Path**|**tenantId**  <br>*可选*|租户id|integer (int64)|
|**Query**|**appId**  <br>*可选*|产品线id|integer (int64)|


#### 响应

|HTTP代码|说明|类型|
|---|---|---|
|**200**|OK|[BaseResponse«string»](#c2b8bd5459ac78f2e4e0011198c1a1d4)|
|**204**|No Content|无内容|
|**401**|Unauthorized|无内容|
|**403**|Forbidden|无内容|


#### 生成

* `\*/*`


#### 标签

* goods-controller


<a name="querytaxnousingget"></a>
### 查询国税信息
```
GET /{tenantId}/enterprise/v1/tax-codes
```


#### 参数

|类型|名称|说明|类型|
|---|---|---|---|
|**Path**|**tenantId**  <br>*必填*|租户id|integer (int64)|
|**Query**|**goodsTaxNo**  <br>*可选*|税编|string|
|**Query**|**itemName**  <br>*可选*|商品简称|string|


#### 响应

|HTTP代码|说明|类型|
|---|---|---|
|**200**|OK|[BaseResponse«List«TaxCodeRecord»»](#37e4e3c03ee8878a83de679114811afa)|
|**401**|Unauthorized|无内容|
|**403**|Forbidden|无内容|
|**404**|Not Found|无内容|


#### 生成

* `\*/*`


#### 标签

* tax-code-controller


<a name="createtaxnumberusingpost"></a>
### 新增税编信息
```
POST /{tenantId}/enterprise/v1/tax-numbers
```


#### 参数

|类型|名称|说明|类型|
|---|---|---|---|
|**Path**|**tenantId**  <br>*可选*|租户id|integer (int64)|
|**Query**|**appId**  <br>*必填*|产品线id|integer (int64)|
|**Query**|**goodsId**  <br>*必填*|商品id|integer (int64)|
|**Body**|**taxNumbers**  <br>*必填*|税编信息|< [TaxNumber](#taxnumber) > array|


#### 响应

|HTTP代码|说明|类型|
|---|---|---|
|**200**|OK|[BaseResponse«string»](#c2b8bd5459ac78f2e4e0011198c1a1d4)|
|**201**|Created|无内容|
|**401**|Unauthorized|无内容|
|**403**|Forbidden|无内容|
|**404**|Not Found|无内容|


#### 消耗

* `application/json`


#### 生成

* `\*/*`


#### 标签

* tax-number-controller


<a name="querytaxnousingget_1"></a>
### 查询税编详情
```
GET /{tenantId}/enterprise/v1/tax-numbers/{conversionCode}
```


#### 参数

|类型|名称|说明|类型|
|---|---|---|---|
|**Path**|**conversionCode**  <br>*可选*|商品编码|string|
|**Path**|**tenantId**  <br>*必填*|租户id|integer (int64)|
|**Query**|**appId**  <br>*必填*|产品线id|integer (int64)|
|**Query**|**goodsTypeCode**  <br>*必填*|商品类型code|string|
|**Query**|**providerTenantId**  <br>*可选*|供应商租户id|integer (int64)|


#### 响应

|HTTP代码|说明|类型|
|---|---|---|
|**200**|OK|[BaseResponse«GoodsDetail»](#746617118ea1b1a50eb86f6057507377)|
|**401**|Unauthorized|无内容|
|**403**|Forbidden|无内容|
|**404**|Not Found|无内容|


#### 生成

* `\*/*`


#### 标签

* tax-number-controller


<a name="updatetaxnumberusingput"></a>
### 修改税编信息
```
PUT /{tenantId}/enterprise/v1/tax-numbers/{id}
```


#### 参数

|类型|名称|说明|类型|
|---|---|---|---|
|**Path**|**id**  <br>*必填*|税编id|integer (int64)|
|**Path**|**tenantId**  <br>*可选*|租户id|integer (int64)|
|**Query**|**appId**  <br>*可选*|产品线id|integer (int64)|
|**Body**|**taxNumber**  <br>*必填*|税编信息|[TaxNumber](#taxnumber)|


#### 响应

|HTTP代码|说明|类型|
|---|---|---|
|**200**|OK|[BaseResponse«string»](#c2b8bd5459ac78f2e4e0011198c1a1d4)|
|**201**|Created|无内容|
|**401**|Unauthorized|无内容|
|**403**|Forbidden|无内容|
|**404**|Not Found|无内容|


#### 消耗

* `application/json`


#### 生成

* `\*/*`


#### 标签

* tax-number-controller


<a name="deletetaxnumberusingdelete"></a>
### 删除税编信息
```
DELETE /{tenantId}/enterprise/v1/tax-numbers/{id}
```


#### 参数

|类型|名称|说明|类型|
|---|---|---|---|
|**Path**|**id**  <br>*必填*|税编id|integer (int64)|
|**Path**|**tenantId**  <br>*可选*|租户id|integer (int64)|
|**Query**|**appId**  <br>*可选*|产品线id|integer (int64)|


#### 响应

|HTTP代码|说明|类型|
|---|---|---|
|**200**|OK|[BaseResponse«string»](#c2b8bd5459ac78f2e4e0011198c1a1d4)|
|**204**|No Content|无内容|
|**401**|Unauthorized|无内容|
|**403**|Forbidden|无内容|


#### 生成

* `\*/*`


#### 标签

* tax-number-controller




<a name="definitions"></a>
## 定义

<a name="746617118ea1b1a50eb86f6057507377"></a>
### BaseResponse«GoodsDetail»

|名称|类型|
|---|---|
|**code**  <br>*可选*|string|
|**message**  <br>*可选*|string|
|**result**  <br>*可选*|[GoodsDetail](#goodsdetail)|


<a name="6320a621975b3f52a1bae3b3ba4cede5"></a>
### BaseResponse«GoodsPage»

|名称|类型|
|---|---|
|**code**  <br>*可选*|string|
|**message**  <br>*可选*|string|
|**result**  <br>*可选*|[GoodsPage](#goodspage)|


<a name="37e4e3c03ee8878a83de679114811afa"></a>
### BaseResponse«List«TaxCodeRecord»»

|名称|类型|
|---|---|
|**code**  <br>*可选*|string|
|**message**  <br>*可选*|string|
|**result**  <br>*可选*|< [TaxCodeRecord](#taxcoderecord) > array|


<a name="c2b8bd5459ac78f2e4e0011198c1a1d4"></a>
### BaseResponse«string»

|名称|类型|
|---|---|
|**code**  <br>*可选*|string|
|**message**  <br>*可选*|string|
|**result**  <br>*可选*|string|


<a name="creategoodsparam"></a>
### CreateGoodsParam

|名称|说明|类型|
|---|---|---|
|**goods**  <br>*必填*|商品信息|[Goods](#goods)|
|**taxNumbers**  <br>*可选*|税转信息|< [TaxNumber](#taxnumber) > array|


<a name="creategoodstypeparam"></a>
### CreateGoodsTypeParam

|名称|说明|类型|
|---|---|---|
|**goodsTypeInfo**  <br>*必填*|商品类型信息|[GoodsTypeInfo](#goodstypeinfo)|


<a name="goods"></a>
### Goods

|名称|说明|类型|
|---|---|---|
|**goodsName**  <br>*必填*|商品名称|string|
|**goodsNo**  <br>*必填*|商品编码|string|
|**goodsTypeCode**  <br>*必填*|商品类型|string|
|**orgId**  <br>*可选*|所属组织|string|
|**providerCompanyName**  <br>*可选*|供应商公司名称|string|
|**providerTenantId**  <br>*可选*|供应商租户id|integer (int64)|
|**providerTenantName**  <br>*可选*|供应商租户名称|string|
|**quantityUnit**  <br>*可选*|单位|string|
|**specification**  <br>*可选*|规格|string|
|**unitPrice**  <br>*可选*|单价|number|


<a name="goodsdetail"></a>
### GoodsDetail

|名称|说明|类型|
|---|---|---|
|**goods**  <br>*可选*|商品信息|[Goods](#goods)|
|**mappingGoods**  <br>*可选*|映射商品信息|< [Goods](#goods) > array|
|**taxNumbers**  <br>*可选*|税编信息|< [TaxNumberRecord](#taxnumberrecord) > array|


<a name="goodspage"></a>
### GoodsPage

|名称|说明|类型|
|---|---|---|
|**goodsRecords**  <br>*可选*|商品记录|< [GoodsRecord](#goodsrecord) > array|
|**total**  <br>*可选*|总条数|integer (int64)|


<a name="goodsrecord"></a>
### GoodsRecord

|名称|说明|类型|
|---|---|---|
|**goodsName**  <br>*必填*|商品名称|string|
|**goodsNo**  <br>*必填*|商品编码|string|
|**goodsTypeCode**  <br>*必填*|商品类型|string|
|**id**  <br>*可选*|主键|integer (int64)|
|**orgId**  <br>*可选*|所属组织|string|
|**providerCompanyName**  <br>*可选*|供应商公司名称|string|
|**providerTenantId**  <br>*可选*|供应商租户id|integer (int64)|
|**providerTenantName**  <br>*可选*|供应商租户名称|string|
|**quantityUnit**  <br>*可选*|单位|string|
|**specification**  <br>*可选*|规格|string|
|**taxNumbers**  <br>*可选*|税编信息|< [TaxNumber](#taxnumber) > array|
|**unitPrice**  <br>*可选*|单价|number|


<a name="goodstypeinfo"></a>
### GoodsTypeInfo

|名称|说明|类型|
|---|---|---|
|**appId**  <br>*必填*|产品线id|integer (int64)|
|**appName**  <br>*必填*|产品线名称|string|
|**category**  <br>*必填*|商品类型|enum (0, 1)|
|**tenantId**  <br>*可选*|租户id|integer (int64)|
|**tenantName**  <br>*可选*|租户名称|string|
|**typeCode**  <br>*可选*|类型代码|string|
|**typeName**  <br>*可选*|类型名称|string|


<a name="relationparams"></a>
### RelationParams

|名称|说明|类型|
|---|---|---|
|**goodsId**  <br>*可选*|商品id|integer (int64)|
|**mappingGoodsIds**  <br>*可选*|映射商品id|< integer (int64) > array|


<a name="taxcoderecord"></a>
### TaxCodeRecord

|名称|说明|类型|
|---|---|---|
|**goodsTaxNo**  <br>*可选*|税编|string|
|**itemName**  <br>*可选*|简称|string|
|**taxPre**  <br>*可选*|是否享受优惠政策, 0=否， 1=是|string|
|**taxPreCon**  <br>*可选*|优惠政策内容|string|
|**taxRate**  <br>*可选*|税率|number|
|**zeroTax**  <br>*可选*|零税率标识|string|


<a name="taxnumber"></a>
### TaxNumber

|名称|说明|类型|
|---|---|---|
|**conversionCode**  <br>*必填*|税编转换代码|string|
|**defaultTaxCode**  <br>*必填*|是否默认税编|enum (0, 1)|
|**taxCode**  <br>*必填*|税收分类编码|string|
|**taxName**  <br>*必填*|税编名称|string|
|**taxPre**  <br>*必填*|是否享受优惠政策|enum (0, 1)|
|**taxPreCon**  <br>*可选*|优惠政策内容|string|
|**taxRate**  <br>*必填*|税率|number|
|**taxShorName**  <br>*必填*|税编简称|string|
|**zeroTax**  <br>*可选*|零税率标识|enum (0, 1, 2, 3)|


<a name="taxnumberrecord"></a>
### TaxNumberRecord

|名称|说明|类型|
|---|---|---|
|**conversionCode**  <br>*必填*|税编转换代码|string|
|**defaultTaxCode**  <br>*必填*|是否默认税编|enum (0, 1)|
|**id**  <br>*可选*|id|integer (int64)|
|**taxCode**  <br>*必填*|税收分类编码|string|
|**taxName**  <br>*必填*|税编名称|string|
|**taxPre**  <br>*必填*|是否享受优惠政策|enum (0, 1)|
|**taxPreCon**  <br>*可选*|优惠政策内容|string|
|**taxRate**  <br>*必填*|税率|number|
|**taxShorName**  <br>*必填*|税编简称|string|
|**zeroTax**  <br>*可选*|零税率标识|enum (0, 1, 2, 3)|





