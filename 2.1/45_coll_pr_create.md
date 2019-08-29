# 新增担保信息-房产
## 描述
个人、企业的融资申请新增房产担保信息（所有者至少存在一个）。

## API代码
loan\_app:coll_pr:create

## 请求参数
| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- | 
| appId | String | 是 | 50 | 申请ID（[融资申请创建API](20_app_push.md)返回的结果） | 0092728480d24f5d87bf63639b5cfe1c |
| mtCollStyleCd | String | 是 | 20 | 担保方式(BZ-保证;DY-抵押;ZY-质押;XY-信用) | DY |
| mtCollTypCd | String | 是 | 20 | 担保类型 | PR |
| mtCollCatCd | String | 是 | 20 | 担保品种 | PR01 |
| mtCollCd | String | 是 | 20 | 担保小类 | DY0101001 |
| collValue | Number | 是 | 20(18,2) | 内部评估价格 | 123456.78 |
| dtPurchased | Date | 是 | - | 购买时间 | 2017-01-01 |
| mortgageInfo | String | 否 | 200 | 抵押摘要 |  |
| purchasedPrc | Number | 否 | 200 | 购买价值 |  |
| appCollPr | JSON | 是 | - | 房产担保品信息， 见[房产担保品信息](#房产担保品信息) |
| collEvaluate | JSON(List) | 否 | - | 担保评估信息， 见[担保评估信息](#担保评估信息) |
| csCollOwner | JSON(List) | 否（所有者至少存在一个） | - | 担保所有者信息（个人）， 见[担保所有者信息（个人）](#担保所有者信息个人) |
| cpCollOwner | JSON(List) | 否（所有者至少存在一个） | - | 担保所有者信息（企业）， 见[担保所有者信息（企业）](#担保所有者信息企业) |


### 房产担保品信息
| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| prBasicInfo | JSON | 是 | - | 房产基本信息， 见[房产基本信息](#房产基本信息) |
| prConsttInfo | JSON | 是 | - | 房屋构造情况， 见[房屋构造情况](#房屋构造情况) |
| prLandInfo | JSON | 是 | - | 土地状况， 见[土地状况](#土地状况) |
| prLeaseInfo | JSON | 是 | - | 租赁信息， 见[租赁信息](#租赁信息) |
| prRecordInfo | JSON | 是 | - | 房屋登记情况， 见[房屋登记情况](#房屋登记情况) |

### 房产基本信息
| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| buildingNm | String | 是 | 50 | 建筑物名称 |   |
| mtCollShareCd | String | 是 | - | 共有情况(单独所有:001，共同所有:002，按份所有:003) | 001 |
| addrLine | String | 是 | 100 | 房屋坐落 |   |
| contractNo | String | 否 | 30 | 房地产买卖合同编号(房产证号与房地产买卖合同编号二者至少填写一个) |   |
| propertyNo | String | 否 | 30 | 房产证号(房产证号与房地产买卖合同编号二者至少填写一个) |   |
| dtRecord | Date | 是 | - | 登记日期 | 2017-01-01 |
| age | number | 是 | 4  | 房龄 |   |
| dtFinished | Date | 是 | - | 竣工日期 | 2017-01-01  |
| hasElevator | String | 是 | 20 | 是否有电梯 |   |
| monthPropertyFee | String | 否 | 12  | 月物业费 |  |
| mtPrtyFacingCd | String | 是 | - | 房屋朝向(南北:001,正南:002,东南:003,东向:004,西南:005,西向:006,东北:007,西北:008,北向:009) | 001  |
| mtPrtyUseCd | String | 是 | - | 规划用途(商铺:001,写字楼:002,宾馆酒店:003,商场:004,豪宅/别墅:005,高档商品用房:006,普通民宅:007,经济适用房:008,生产厂房:009,辅助设施用房:010,库房:011,其他:999) | 001 |
| otherPrtyUseDscp | String | 是 | 30 | 规划用途（其他）,当“规划用途”选择“其他”时，填写此字段 | 工业用地  |
| propertyCompany | String | 是 | 50  | 物业公司 |   |

### 房屋构造情况
| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| mtConsttFlrCd | String | 否 | - | 地面构造(现浇:001,预制:002,其他:003)| 001 |
| mtConsttRoofCd| String | 否 | - | 屋顶构造(现浇:001,预制:002,其他:003) | 001 |
| mtConsttWallCd| String | 否 | -  | 墙壁构造(钢混:001,砖混:002,其他:003) | 001 |
| otherConsttFlrDscp | String | 否 | 30  | 地面构造（其他）,地面构造为其他时填写 |   |
| otherConsttRoofDscp | String | 否 | 30  | 屋顶构造（其他）,屋顶构造为其他时填写 |   |
| otherConsttWallDscp| String | 否 | 30  | 墙壁构造（其他）,墙壁构造为其他时填写 |   |
|  remark | String | 否 | 200 | 建筑物说明 |   |

### 土地状况
| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| dtLandEnd | Date | 否 | - | 土地使用结束时间 | 2017-01-02  |
| dtLandStarted| Date | 否 | - | 土地使用起始时间 | 2087-01-01  |
| landNo| String | 否 |  30 | 地号 | KL92819928177281  |
| landUseLife | number | 否 | 3 | 土地使用年限 | 70 |
| mtLandAcquireMtdCd | String | 否 | - | 土地使用权取得方式(划拨:001,出让:002,转让:003,其他:999) | 001 |
| otherLandAcquireMtdDscp| String | 否 | 30  | 土地使用权取得方式（其他）,土地使用权取得方式为其他时填写 |   |

### 租赁信息
| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| dtEffective | Date | 否 | -  | 租赁开始日期(是否租赁为Y时填写) | 2017-01-01 |
| isLease | String | 是 |  -  | 是否租赁(Y=是 N=否) | Y |
| lesseeNm | String | 否 |  80  | 租人名称(是否租赁为Y时填写) | 张三 |

### 房屋登记情况
| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| buildingNo | number | 否 | 5 | 楼号或幢号 | 5 |
| builtUpArea | number | 是 | 7 | 建筑面积(单位平米㎡) | 123.5  |
| floorNo | number | 是 | 3 | 所在层数 | 12 |
| housingBalconyArea | number | 否 |7 | 阳台建筑面积(单位平米㎡) | 123.5  |
| housingCoveredArea | number | 否 |7 | 套内建筑面积（含阳台,单位平米㎡） |  123.5 |
| housingShareArea | number | 否 | 7 | 共有分摊建筑面积(单位平米㎡) |  123.5 |
| housingUsefulArea | number | 否 | 7 | 使用面积(单位平米㎡) | 123.5  |
| roomNo | number | 是 |  20 | 房号 | 12 |
| roomNum | number | 是 | 5  | 套数或间数 | 10 |
| structure | String | 是 |  20 | 结构 | 砖混结构 |
| totalFloorNum | number | 是 | 3 | 房屋总层数 | 15 |

### 担保评估信息
| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| evaluateValue | Number | 否 | 20(18,2) | 评估师核定价格 | 123456.78 |
| dtEvaluated | Date | 否 | - | 评估时间 | 2017-05-03 |
| appraiser | String | 否 | 50 | 评估师 | 李四 |

### 担保所有者信息（个人）
| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| nm | String | 是 | 300 | 所有者姓名 | 张三 |
| mtCifIdTypCd | String | 是 | 20 | 证件类型(身份证:I,护照:I2,军人证:I3,港澳台身份证:I4,武警证:I5,警官证:I6,其他:999) | I |
| idNo | String | 是 | 50 | 证件号码 | 110113198410126933 |
| mobileNo | String | 是 | 20 | 联系方式 | 13512341234 |

### 担保所有者信息（企业）
| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| nm | String | 是 | 80 | 企业名称(与营业执照上一致) | 北京某某公司 |
| idNo | String | 是 | 18 | 营业执照号 或者 统一社会信用代码 | 893097600399759163 |
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
    "appId": "1cb929f989fd4175bf6e4bf79a3ed422",
    "mtCollStyleCd": "BZ", 
    "mtCollTypCd":"PR",
    "mtCollCatCd": "PR01",
    "mtCollCd": "DY0101001",
    "collValue": 123456.78,
    "dtPurchased": "2017-01-01",
    "mortgageInfo": "抵押",
    "purchasedPrc": 20000,
	"appCollPr": 
        {
            "prBasicInfo":{
                "buildingNm":"朝外SOHO",
                "mtCollShareCd":"001",
                "addrLine":"北京",
                "dtRecord":"2017-01-01",
                "age":10,
                "dtFinished":"2017-01-01",
                "hasElevator":"Y",
                "monthPropertyFee":"200",
                "mtPrtyFacingCd":"001",
                "mtPrtyUseCd":"001",
                "otherPrtyUseDscp":"工业用地",
                "propertyCompany":"物业公司",
                "contractNo":"1672887162761726YJK",
                "propertyNo":"9388287717622271HYG"
            },
            "prConsttInfo":{
                "mtConsttFlrCd":"003",
                "mtConsttRoofCd":"003",
                "mtConsttWallCd":"003",
                "otherConsttFlrDscp":"工业用地",
                "otherConsttRoofDscp":"工业用地",
                "otherConsttWallDscp":"工业用地",
                "remark":"说明信息"
            },
            "prLandInfo":{
                "dtLandEnd":"2017-01-02",
                "dtLandStarted":"2087-01-01",
                "landNo":"KL92819928177281",
                "landUseLife":70,
                "mtLandAcquireMtdCd":"001",
                "otherLandAcquireMtdDscp":"继承"
            },
            "prLeaseInfo":{
                "dtEffective":"2017-01-01",
                "isLease":"Y",
                "lesseeNm":"张三"
            },
            "prRecordInfo":{
                "buildingNo":"5",
                "builtUpArea":"123.5",
                "floorNo":"12",
                "housingBalconyArea":"123.5",
                "housingCoveredArea":"123.5",
                "housingShareArea":"123.5",
                "housingUsefulArea":"123.5",
                "roomNo":"287",
                "roomNum":"12",
                "structure":"砖混结构",
                "totalFloorNum":"15"
            }
        },
    "collEvaluate": [
        {
            "evaluateValue": 123456.78, 
            "dtEvaluated": "2017-05-03",
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
    "appId":"0092728480d24f5d87bf63639b5cfe1c",
    "collId":"ad8b4a0f71cc11e7a58000ff9ef96c80"
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