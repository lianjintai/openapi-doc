# 新增担保信息-房产
## 描述
个人、企业的融资申请新增房产担保信息（所有者至少存在一个）。

## API代码
loan\_app:coll_pr:create

## 请求参数
| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | 
| appId | String | 是 | 50 | 申请ID（[融资申请创建API](20_app_push.md)返回的结果） | 0092728480d24f5d87bf63639b5cfe1c |
| mtCollStyleCd | String | 是 | 20 | 担保方式 | BZ-保证;DY-抵押;ZY-质押;XY-信用 |
| mtCollCatCd | String | 是 | 20 | 担保品种 | PR01 |
| mtCollCd | String | 是 | 20 | 担保小类 | DY0101001 |
| collValue | Number | 是 | 20(18,2) | 担保品价值 | 123456.78 |
| 担保详情字段（开发人员添加） | String | - | - | 担保详情字段描述（开发人员添加） |  |
| collEvaluate | JSON(List) | 否 | - | 担保评估信息， 见[担保评估信息](#担保评估信息) |
| csCollOwner | JSON(List) | 否（所有者至少存在一个） | - | 担保所有者信息（个人）， 见[担保所有者信息（个人）](#担保所有者信息（个人）) |
| cpCollOwner | JSON(List) | 否（所有者至少存在一个） | - | 担保所有者信息（企业）， 见[担保所有者信息（企业）](#担保所有者信息（企业）) |

### 担保评估信息
| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| evaluateValue | Number | 否 | 20(18,2) | 评估师核定价格 | 123456.78 |
| dtEvaluated | Date | 否 | - | 评估时间 | 2017-05-03 15:12:24 |
| appraiser | String | 否 | 50 | 评估师 | 李四 |

### 担保所有者信息（个人）
| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| nm | String | 是 | 300 | 借款人姓名（与身份证上相同） | 张三 |
| mtCifIdTypCd | String | 是 | 20 | 证件类型 | I |
| idNo | String | 是 | 50 | 身份证号码 | 110113198410126933 |
| mobileNo | String | 是 | 20 | 联系方式 | 13512341234 |

### 担保所有者信息（企业）
| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| nm | String | 是 | 300 | 企业名称(与营业执照上一致) | 北京某某公司 |
| idNo | String | 是 | 50 | 统一社会信用代码／营业执照号 | 893097600399759163 |
| isComb | String | 是 | 1 | 是否三证合一（Y是 N否） | Y |

## 响应参数
| 名称 | 类型 | 描述 |示例值 |
| --- | --- | --- | --- |
| appId | String | 申请ID | 0092728480d24f5d87bf63639b5cfe1c |
| collId | String | 担保品ID | ad8b4a0f71cc11e7a58000ff9ef96c80 |

## 错误码
| 描述 | HTTP状态码 | 语义 |
| --- | --- | --- | 
| appId未找到 | 400 | 请输入正确的app_id,或检查申请类型与申请ID是否匹配 |
| mtCollCatCd必填 | 400 | 担保品种为空 |
| 所有者未填写 | 400 | 所有者至少存在一个 |

## 示例
### 请求示例
```javascript
{
	"app_id": "0092728480d24f5d87bf63639b5cfe1c", 
	"mtCollStyleCd": "DY", 
	"mtCollCatCd": "PR01", 
	"mtCollCd": "DY0101001", 
	"collValue": 123456.78, 
    "collEvaluate": [
        {
            "evaluateValue": 123456.78, 
            "dtEvaluated": "2017-05-03 15:12:24",
            "appraiser": "李四"
        }
    ],
	"csCollOwner": [
        {
            "nm": "张三", 
			"mtCifIdTypCd": "I", 
			"idNo": "110113198410126933", 
            "mobileNo": "13512341234"
        }
    ],
	"cpCollOwner": [
        {
            "nm": "北京某某公司", 
            "idNo": "893097600399759163",
            "isComb": "Y"
        }
    ]
}
```

### 返回示例（正常）
```javascript
{
    "appId":"0092728480d24f5d87bf63639b5cfe1c"
}
```

### 返回示例（异常）
```javascript
{
  "error": "500",
  "message": "没有获取到用户身份信息",
  "timestamp": "2016-12-29 15:10:32"
}
```


## FAQ
关于此文档暂时还没有FAQ