# 群API


## 获取群列表

GetIslandList

#### 接口

|地址|版本|方式|权限|
|:-----|:---------------|:-----|:---------------|
|`/api/v1/island/list`|<Badge type="warning" text="v1" vertical="middle" />|POST|不需要权限|
 
#### 入参

无

#### 出参

|字段|类型|说明|
|:---------------|:-----|:---------------|
|status|int|[返回码](../start/status.md)|
|message|string|返回信息|
|data|`list<object>`|数据列表|

#### 数据

|字段|类型|说明|
|:---------------|:-----|:---------------|
|islandId|string|群号|
|islandName|string|群名称|
|coverUrl|string|群头像|
|memberCount|int|群总人数|
|onlineMemberCount|int|群在线人数|
|defaultChannelId|string|默认访问频道ID|
|systemChannelId|string|系统消息频道ID|

#### 出参示例

```json
{
    "status": 0,
    "message": "success",
    "data": [{
            "islandId": "10001",
            "islandName": "测试群",
            "coverUrl": "https://img.imdodo.com/dodo/730ace7b311879cee67bbbea41018bbe.png",
            "memberCount": 1000,
            "onlineMemberCount": 500,
            "defaultChannelId": "1000101",
            "systemChannelId": "1000102"
        }
    ]
}
```


## 获取群信息

GetIslandInfo

#### 接口

|地址|版本|方式|权限|
|:-----|:---------------|:-----|:---------------|
|`/api/v1/island/info`|<Badge type="warning" text="v1" vertical="middle" />|POST|不需要权限|
 
#### 入参

|字段|类型|必传|说明|
|:---------------|:-----|:-----|:---------------|
|islandId|string|是|群号|

#### 出参

|字段|类型|说明|
|:---------------|:-----|:---------------|
|status|int|[返回码](../start/status.md)|
|message|string|返回信息|
|data|object|返回数据|

#### 数据

|字段|类型|说明|
|:---------------|:-----|:---------------|
|islandId|string|群号|
|islandName|string|群名称|
|coverUrl|string|群头像|
|memberCount|int|群总人数|
|onlineMemberCount|int|群在线人数|
|description|string|群简介|
|defaultChannelId|string|默认访问频道ID|
|systemChannelId|string|系统消息频道ID|

#### 入参示例

```json
{
    "islandId": "10001"
}
```

#### 出参示例

```json
{
    "data": {
        "islandId": "10001",
        "islandName": "测试群",
        "coverUrl": "https://img.imdodo.com/dodo/730ace7b311879cee67bbbea41018bbe.png",
        "memberCount": 1000,
        "onlineMemberCount": 500,
        "description": "这个是一个测试群",
        "defaultChannelId": "1000101",
        "systemChannelId": "1000102",
    },
    "status": 0,
    "message": "success"
}
```


## 获取群等级排行榜

GetIslandLevelRankList

::: tip
只对开通了群等级的群有效
:::

#### 接口

|地址|版本|方式|权限|
|:-----|:---------------|:-----|:---------------|
|`/api/v1/island/level/rank/list`|<Badge type="warning" text="v1" vertical="middle" />|POST|不需要权限|
 
#### 入参

|字段|类型|必传|说明|
|:---------------|:-----|:-----|:---------------|
|islandId|string|是|群号|

#### 出参

|字段|类型|说明|
|:---------------|:-----|:---------------|
|status|int|[返回码](../start/status.md)|
|message|string|返回信息|
|data|`list<object>`|数据列表|

#### 数据

|字段|类型|说明|
|:---------------|:-----|:---------------|
|dodoId|string|DoDo号|
|nickName|string|群昵称|
|level|int|等级|
|rank|int|排名，返回前100名|

#### 入参示例

```json
{
    "islandId": "10001"
}
```

#### 出参示例

```json
{
    "status": 0,
    "message": "success",
    "data": [{
            "dodoId": "666666",
            "nickName": "测试群昵称",
            "level": 1,
            "rank": 1,
        }
    ]
}
```


## 获取群禁言名单

GetIslandMuteList

#### 接口

|地址|版本|方式|权限|
|:-----|:---------------|:-----|:---------------|
|`/api/v1/island/mute/list`|<Badge type="warning" text="v1" vertical="middle" />|POST|成员管理-管理成员|
 
#### 入参

|字段|类型|必传|说明|
|:---------------|:-----|:-----|:---------------|
|islandId|string|是|群号|
|pageSize|int|是|页大小，最大100|
|maxId|long|是|上一页最大ID值，为提升分页查询性能，需要传入上一页查询记录中的最大ID值，首页请传0|

#### 数据

|字段|类型|说明|
|:---------------|:-----|:---------------|
|maxId|object|最大ID值|
|list|`list<object>`|数据列表|

#### 列表项

|字段|类型|说明|
|:---------------|:-----|:---------------|
|dodoId|string|DoDo号|

#### 入参示例

```json
{
    "islandId": "10001",
    "pageSize": 100,
    "maxId": 0,
}
```

#### 出参示例

```json
{
    "data": {
        "maxId": 12345,
        "list": [{
                "dodoId": "666666"
            }
        ]
    },
    "status": 0,
    "message": "success"
}
```


## 获取群封禁名单

GetIslandBanList

#### 接口

|地址|版本|方式|权限|
|:-----|:---------------|:-----|:---------------|
|`/api/v1/island/ban/list`|<Badge type="warning" text="v1" vertical="middle" />|POST|成员管理-管理成员|
 
#### 入参

|字段|类型|必传|说明|
|:---------------|:-----|:-----|:---------------|
|islandId|string|是|群号|
|pageSize|int|是|页大小，最大100|
|maxId|long|是|上一页最大ID值，为提升分页查询性能，需要传入上一页查询记录中的最大ID值，首页请传0|

#### 数据

|字段|类型|说明|
|:---------------|:-----|:---------------|
|maxId|object|最大ID值|
|list|`list<object>`|数据列表|

#### 列表项

|字段|类型|说明|
|:---------------|:-----|:---------------|
|dodoId|string|DoDo号|

#### 入参示例

```json
{
    "islandId": "10001",
    "pageSize": 100,
    "maxId": 0,
}
```

#### 出参示例

```json
{
    "data": {
        "maxId": 12345,
        "list": [{
                "dodoId": "666666"
            }
        ]
    },
    "status": 0,
    "message": "success"
}
```