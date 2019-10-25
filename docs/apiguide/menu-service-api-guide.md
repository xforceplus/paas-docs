# 企业SAAS平台规则配置接口列表


<a name="overview"></a>
## 概览

### 版本信息
*版本* : 1.0.0


### URI scheme
*域名* : menu-service-fat-svc.phoenix-t.xforceplus.com  
*基础路径* : /


### 标签

* menu-controller : the Menu Service API
* setting-controller : the App Setting Service API




<a name="paths"></a>
## 路径

<a name="editmenuusingpost"></a>
### 编辑菜单信息
```
POST /menu
```


#### 参数

|类型|名称|说明|类型|
|---|---|---|---|
|**Body**|**data**  <br>*可选*|编辑菜单信息请求消息体|[ReqEditMenu](#reqeditmenu)|


#### 响应

|HTTP代码|说明|类型|
|---|---|---|
|**200**|标准返回消息体|[ResStandard](#resstandard)|
|**201**|Created|无内容|
|**401**|Unauthorized|无内容|
|**403**|Forbidden|无内容|
|**404**|Not Found|无内容|


#### 消耗

* `application/json`


#### 生成

* `application/json`


#### 标签

* menu-controller


<a name="resortmenususingpost"></a>
### 菜单树结构调整接口
```
POST /menu-resort/{systemId}
```


#### 参数

|类型|名称|说明|类型|
|---|---|---|---|
|**Path**|**systemId**  <br>*必填*|系统Id|string|
|**Body**|**data**  <br>*可选*|修改菜单前端静态资源请求消息体|< [ReqEditMenu](#reqeditmenu) > array|


#### 响应

|HTTP代码|说明|类型|
|---|---|---|
|**200**|标准返回消息体|[ResStandard](#resstandard)|
|**201**|Created|无内容|
|**401**|Unauthorized|无内容|
|**403**|Forbidden|无内容|
|**404**|Not Found|无内容|


#### 消耗

* `application/json`


#### 生成

* `application/json`


#### 标签

* menu-controller


<a name="updatemenuresourcesusingpost"></a>
### 菜单模块静态资源回调接口
```
POST /menu-resources
```


#### 参数

|类型|名称|说明|类型|
|---|---|---|---|
|**Body**|**data**  <br>*可选*|修改菜单前端静态资源请求消息体|[ReqMenuResources](#reqmenuresources)|


#### 响应

|HTTP代码|说明|类型|
|---|---|---|
|**200**|标准返回消息体|[ResStandard](#resstandard)|
|**201**|Created|无内容|
|**401**|Unauthorized|无内容|
|**403**|Forbidden|无内容|
|**404**|Not Found|无内容|


#### 消耗

* `application/json`


#### 生成

* `application/json`


#### 标签

* menu-controller


<a name="deletemenuusingdelete"></a>
### 删除菜单信息
```
DELETE /menu/{systemId}/{id}
```


#### 参数

|类型|名称|说明|类型|
|---|---|---|---|
|**Path**|**id**  <br>*必填*|菜单id|string|
|**Path**|**systemId**  <br>*必填*|系统id|string|


#### 响应

|HTTP代码|说明|类型|
|---|---|---|
|**200**|标准返回消息体|[ResStandard](#resstandard)|
|**204**|No Content|无内容|
|**401**|Unauthorized|无内容|
|**403**|Forbidden|无内容|


#### 生成

* `application/json`


#### 标签

* menu-controller


<a name="getmenususingget"></a>
### 查询菜单列表
```
GET /menus/{systemId}
```


#### 参数

|类型|名称|说明|类型|
|---|---|---|---|
|**Path**|**systemId**  <br>*必填*|系统id|string|


#### 响应

|HTTP代码|说明|类型|
|---|---|---|
|**200**|返回菜单树结构|[ResAllMenus](#resallmenus)|
|**401**|Unauthorized|无内容|
|**403**|Forbidden|无内容|
|**404**|Not Found|无内容|


#### 生成

* `application/json`


#### 标签

* menu-controller


<a name="editappsettingusingpost"></a>
### 编辑app配置信息
```
POST /setting
```


#### 参数

|类型|名称|说明|类型|
|---|---|---|---|
|**Body**|**data**  <br>*可选*|编辑app配置信息请求消息体|[ReqEditAppSetting](#reqeditappsetting)|


#### 响应

|HTTP代码|说明|类型|
|---|---|---|
|**200**|标准返回消息体|[ResStandard](#resstandard)|
|**201**|Created|无内容|
|**401**|Unauthorized|无内容|
|**403**|Forbidden|无内容|
|**404**|Not Found|无内容|


#### 消耗

* `application/json`


#### 生成

* `application/json`


#### 标签

* setting-controller


<a name="deleteappsettingusingdelete"></a>
### 删除app配置信息
```
DELETE /setting/{id}
```


#### 参数

|类型|名称|说明|类型|
|---|---|---|---|
|**Path**|**id**  <br>*必填*|菜单id|string|


#### 响应

|HTTP代码|说明|类型|
|---|---|---|
|**200**|标准返回消息体|[ResStandard](#resstandard)|
|**204**|No Content|无内容|
|**401**|Unauthorized|无内容|
|**403**|Forbidden|无内容|


#### 生成

* `application/json`


#### 标签

* setting-controller


<a name="getappsettingsusingget"></a>
### 查询app配置列表
```
GET /settings
```


#### 响应

|HTTP代码|说明|类型|
|---|---|---|
|**200**|返回app配置列表|[ResAppSettings](#resappsettings)|
|**401**|Unauthorized|无内容|
|**403**|Forbidden|无内容|
|**404**|Not Found|无内容|


#### 生成

* `application/json`


#### 标签

* setting-controller


<a name="editapptenantsettingusingpost"></a>
### 编辑app-tenant配置信息
```
POST /tenant-setting
```


#### 参数

|类型|名称|说明|类型|
|---|---|---|---|
|**Body**|**data**  <br>*可选*|编辑app-tenant配置信息请求消息体|[ReqEditAppTenantSetting](#reqeditapptenantsetting)|


#### 响应

|HTTP代码|说明|类型|
|---|---|---|
|**200**|标准返回消息体|[ResStandard](#resstandard)|
|**201**|Created|无内容|
|**401**|Unauthorized|无内容|
|**403**|Forbidden|无内容|
|**404**|Not Found|无内容|


#### 消耗

* `application/json`


#### 生成

* `application/json`


#### 标签

* setting-controller


<a name="deleteapptenantsettingusingdelete"></a>
### 删除app-tenant配置信息
```
DELETE /tenant-setting/{systemId}/{id}
```


#### 参数

|类型|名称|说明|类型|
|---|---|---|---|
|**Path**|**id**  <br>*必填*|菜单id|string|
|**Path**|**systemId**  <br>*必填*|系统id|string|


#### 响应

|HTTP代码|说明|类型|
|---|---|---|
|**200**|标准返回消息体|[ResStandard](#resstandard)|
|**204**|No Content|无内容|
|**401**|Unauthorized|无内容|
|**403**|Forbidden|无内容|


#### 生成

* `application/json`


#### 标签

* setting-controller


<a name="getapptenantsettingsusingget"></a>
### 查询app-tenant配置列表
```
GET /tenant-settings/{systemId}
```


#### 参数

|类型|名称|说明|类型|
|---|---|---|---|
|**Path**|**systemId**  <br>*必填*|系统id|string|


#### 响应

|HTTP代码|说明|类型|
|---|---|---|
|**200**|返回app-tenant配置列表|[ResAppTenantSettings](#resapptenantsettings)|
|**401**|Unauthorized|无内容|
|**403**|Forbidden|无内容|
|**404**|Not Found|无内容|


#### 生成

* `application/json`


#### 标签

* setting-controller


<a name="uploadimgusingpost"></a>
### logo图标及favicon图标上传
```
POST /upload-image/{type}/{id}
```


#### 参数

|类型|名称|说明|类型|
|---|---|---|---|
|**Path**|**id**  <br>*必填*|配置id|string|
|**Path**|**type**  <br>*必填*|图片类型(icon/favicon)|string|
|**FormData**|**image**  <br>*可选*|上传文件对象|file|


#### 响应

|HTTP代码|说明|类型|
|---|---|---|
|**200**|返回app配置列表|[ResStandard](#resstandard)|
|**201**|Created|无内容|
|**401**|Unauthorized|无内容|
|**403**|Forbidden|无内容|
|**404**|Not Found|无内容|


#### 消耗

* `multipart/form-data`


#### 生成

* `\*/*`


#### 标签

* setting-controller


<a name="uploadtenantimgusingpost"></a>
### 租户定制logo图标及favicon图标上传
```
POST /upload-tenant-image/{type}/{systemId}/{id}
```


#### 参数

|类型|名称|说明|类型|
|---|---|---|---|
|**Path**|**id**  <br>*必填*|配置id|string|
|**Path**|**systemId**  <br>*必填*|系统id|string|
|**Path**|**type**  <br>*必填*|图片类型(icon/favicon)|string|
|**FormData**|**image**  <br>*可选*|上传文件对象|file|


#### 响应

|HTTP代码|说明|类型|
|---|---|---|
|**200**|返回app配置列表|[ResStandard](#resstandard)|
|**201**|Created|无内容|
|**401**|Unauthorized|无内容|
|**403**|Forbidden|无内容|
|**404**|Not Found|无内容|


#### 消耗

* `multipart/form-data`


#### 生成

* `\*/*`


#### 标签

* setting-controller




<a name="definitions"></a>
## 定义

<a name="appsetting"></a>
### AppSetting
app配置信息对象


|名称|类型|
|---|---|
|**appIds**  <br>*可选*|string|
|**createTime**  <br>*可选*|string (date-time)|
|**createUser**  <br>*可选*|string|
|**domain**  <br>*可选*|string|
|**faviconUrl**  <br>*可选*|string|
|**id**  <br>*可选*|string|
|**logoUrl**  <br>*可选*|string|
|**modulesMask**  <br>*可选*|integer (int32)|
|**name**  <br>*可选*|string|
|**theme**  <br>*可选*|string|
|**updateTime**  <br>*可选*|string (date-time)|
|**updateUser**  <br>*可选*|string|


<a name="apptenantsetting"></a>
### AppTenantSetting
app配置信息对象


|名称|类型|
|---|---|
|**appId**  <br>*可选*|integer (int32)|
|**createTime**  <br>*可选*|string (date-time)|
|**createUser**  <br>*可选*|string|
|**faviconUrl**  <br>*可选*|string|
|**id**  <br>*可选*|string|
|**logoUrl**  <br>*可选*|string|
|**modulesMask**  <br>*可选*|integer (int32)|
|**tenantId**  <br>*可选*|string|
|**tenantName**  <br>*可选*|string|
|**theme**  <br>*可选*|string|
|**updateTime**  <br>*可选*|string (date-time)|
|**updateUser**  <br>*可选*|string|


<a name="reqeditappsetting"></a>
### ReqEditAppSetting
编辑app配置信息请求消息体


|名称|类型|
|---|---|
|**appIds**  <br>*可选*|string|
|**domain**  <br>*可选*|string|
|**faviconUrl**  <br>*可选*|string|
|**id**  <br>*可选*|integer (int64)|
|**logoUrl**  <br>*可选*|string|
|**modulesMask**  <br>*可选*|integer (int32)|
|**name**  <br>*可选*|string|
|**theme**  <br>*可选*|string|


<a name="reqeditapptenantsetting"></a>
### ReqEditAppTenantSetting
编辑app配置信息请求消息体


|名称|类型|
|---|---|
|**faviconUrl**  <br>*可选*|string|
|**id**  <br>*可选*|integer (int64)|
|**logoUrl**  <br>*可选*|string|
|**modulesMask**  <br>*可选*|integer (int32)|
|**systemId**  <br>*可选*|integer (int64)|
|**tenantId**  <br>*可选*|integer (int64)|
|**tenantName**  <br>*可选*|string|
|**theme**  <br>*可选*|string|


<a name="reqeditmenu"></a>
### ReqEditMenu
编辑菜单信息请求消息体


|名称|类型|
|---|---|
|**code**  <br>*可选*|string|
|**externalUrl**  <br>*可选*|string|
|**icon**  <br>*可选*|string|
|**id**  <br>*可选*|integer (int64)|
|**isEnable**  <br>*可选*|integer (int32)|
|**name**  <br>*可选*|string|
|**parentId**  <br>*可选*|integer (int64)|
|**resourceCode**  <br>*可选*|string|
|**sortNo**  <br>*可选*|integer (int32)|
|**systemId**  <br>*可选*|integer (int64)|


<a name="reqmenuresources"></a>
### ReqMenuResources
修改菜单前端静态资源请求消息体


|名称|说明|类型|
|---|---|---|
|**assets**  <br>*可选*|文件名列表|string|
|**assetsPath**  <br>*可选*|文件目录|string|
|**code**  <br>*可选*|菜单项目名|string|
|**version**  <br>*可选*|版本号|string|


<a name="resallmenus"></a>
### ResAllMenus
菜单信息返回结果


|名称|说明|类型|
|---|---|---|
|**code**  <br>*可选*|return code|string|
|**message**  <br>*可选*|return message|string|
|**result**  <br>*可选*|return result|< [ResCompleteMenu](#rescompletemenu) > array|


<a name="resappsettings"></a>
### ResAppSettings
app配置信息返回结果


|名称|类型|
|---|---|
|**code**  <br>*可选*|string|
|**message**  <br>*可选*|string|
|**result**  <br>*可选*|< [AppSetting](#appsetting) > array|


<a name="resapptenantsettings"></a>
### ResAppTenantSettings
app-config配置信息返回结果


|名称|类型|
|---|---|
|**code**  <br>*可选*|string|
|**message**  <br>*可选*|string|
|**result**  <br>*可选*|< [AppTenantSetting](#apptenantsetting) > array|


<a name="rescompletemenu"></a>
### ResCompleteMenu
菜单信息对象


|名称|说明|类型|
|---|---|---|
|**appId**  <br>*可选*|应用ID|integer (int32)|
|**assets**  <br>*可选*|静态资源文件列表|string|
|**assetsPath**  <br>*可选*|静态资源文件目录|string|
|**code**  <br>*可选*|菜单项目名|string|
|**createTime**  <br>*可选*|新增时间|string (date-time)|
|**createUser**  <br>*可选*|新增人|string|
|**externalUrl**  <br>*可选*|外部链接URL|string|
|**icon**  <br>*可选*|图标|string|
|**id**  <br>*可选*|id|string|
|**isEnable**  <br>*可选*|启用标记|integer (int32)|
|**name**  <br>*可选*|项目名|string|
|**parentId**  <br>*可选*|父菜单ID|string|
|**resourceCode**  <br>*可选*|资源码|string|
|**sortNo**  <br>*可选*|排序编号|integer (int32)|
|**updateTime**  <br>*可选*|更新时间|string (date-time)|
|**updateUser**  <br>*可选*|更新人|string|
|**version**  <br>*可选*|版本|string|


<a name="resstandard"></a>
### ResStandard
标准返回消息体


|名称|说明|类型|
|---|---|---|
|**code**  <br>*可选*|return code|string|
|**message**  <br>*可选*|return message|string|
|**result**  <br>*可选*|return result|object|





