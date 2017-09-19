# 新增担保信息-机动车
## 描述
个人、企业的融资申请新增机动车担保信息（所有者至少存在一个）。

## API代码
loan\_app:coll_mv:create

## 请求参数
| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- | 
| appId | String | 是 | 50 | 申请ID（[融资申请创建API](20_app_push.md)返回的结果） | 0092728480d24f5d87bf63639b5cfe1c |
| mtCollStyleCd | String | 是 | 20 | 担保方式(BZ-保证;DY-抵押;ZY-质押;XY-信用) | DY |
| mtCollTypCd | String | 是 | 20 | 担保类型 | MV |
| mtCollCatCd | String | 是 | 20 | 担保品种 | MV01 |
| mtCollCd | String | 是 | 20 | 担保小类 | DY0601001 |
| collValue | Number | 是 | 20(18,2) | 担保品价值 | 123456.78 |
| dtPurchased | Date | 是 | - | 购买日期(不可以选择当前日期之后的日期) | 2017-01-01 00:00:00 |
| mortgageInfo | String | 否 | 200 | 抵押摘要 |  |
| purchasedPrc | Number | 是 | 12(10,2) | 购买价格 | 500000.01 ||
| appCollMV | JSON(List) | 是 | - | 机动车担保品详情信息， 见[机动车担保品信息](#机动车担保品信息)||
| csCollOwner | JSON(List) | 个人/企业所有者至少存在一个 | - | 担保所有者信息（个人）， 见[担保所有者信息（个人）][2] ||
| cpCollOwner | JSON(List) | 个人/企业所有者至少存在一个 | - | 担保所有者信息（企业）， 见[担保所有者信息（企业）][3] ||
| collEvaluate | JSON(List) | 否 | - | 机动车担保评估信息， 见[担保评估信息][1] ||

[1]: https://github.com/lianjintai/openapi-doc/blob/dev/2.1/45_coll_pr_create.md#担保评估信息        "担保评估信息" 
[2]: https://github.com/lianjintai/openapi-doc/blob/dev/2.1/45_coll_pr_create.md#担保所有者信息个人        "担保所有者信息（个人）" 
[3]: https://github.com/lianjintai/openapi-doc/blob/dev/2.1/45_coll_pr_create.md#担保所有者信息企业        "担保所有者信息（企业）" 

### 机动车担保品信息
| 名称 | 类型 | 是否必须 | 最大长度 | 描述 |
| --- | --- | --- | --- | --- |
| mvBasicInfo | JSON(List) | 是 | - | 机动车基本信息， 见[机动车基本信息](#机动车基本信息) |
| mvConfInfo | JSON(List) | 是 | - | 车辆配置， 见[车辆配置](#车辆配置) |
| mvInsuranceInfo | JSON(List) | 是 | - | 交强险信息， 见[交强险信息](#交强险信息) |
| mvPaymentInfo | JSON(List) | 是 | - | 代收车船费， 见[代收车船费](#代收车船费) |
| mvPenaltyInfo | JSON(List) | 是 | - | 违章情况， 见[违章情况](#违章情况)|

### 机动车基本信息
| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| dtFirstRecord | Date | 是  |-| 首次登记日期(不可以选择当前日期之后的日期) | 2017-01-01 00:00:00 |
| vehicleType     | String |  是 | 20  | 机动车种类 | 汽车 |
| brand | String | 是  | 30 | 车辆品牌 | 奥迪 |
| approvedMass | Number | 是  | 10(8,2) | 核定载质量(单位：kg，正数，最多保留两位小数) |  1000 |
| approvedPassenger | Number |是| 3 | 核定载客 | 7 |
| color | String | 是  | 10 | 外观颜色 | 红 |
| drivenDistance | Number | 是  | 10 | 行驶里程(单位：km，正数，最多保留两位小数) | 10000 |
| engineCapacity  | Number |  是 | 10(7,3) | 排量(单位：L  ，正数，最多保留三位小数)  | 2.0 |	 
| isMadeInChina   | String |  是 |  - | 产地（Y:国产、N:进口） | N  |
| manufactured    | Date | 是  |-| 出厂日期 | 2017-01-01 00:00:00 |
| model           | String |  是 | 30  | 车型 | 轿车 |
| mtFuelCd        | JSON(List) |  是 | - | 燃料种类（001:汽油、002:柴油、003:混合油、004:天然气、005:电） | 003 |
| power           | Number | 是  | 10 | 功率(单位：KW ，正数 最多保留两位小数) | 100 |
| priceMax        | Number |  是 | 12(10,2)  | 网查价格区间-最大值 | 50000.01 |
| priceMin        | Number | 是  | 12(10,2) | 网查价格区间-最小值 | 50000.01 |
| series          | String | 是  | 30  | 车系 | 美系车 |

### 车辆配置
| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| mtAirconditionTypCd | JSON(List) | 否  | - | 空调控制方式（001:手动、002:自动） | 001 |
| mtCommonConfTypCd | JSON(List) |是| - | 通用配置（001:GPS导航、002:电动天窗、003:全景天窗、004:真皮座椅、005:多功能方向盘、006:无钥匙启动系统、007:无钥匙进入系统、008:蓝牙／车载电话） | 002 |
| mtDriverEleTypCd | JSON(List) | 否  | - | 主／副驾驶座电动调节（001:主、002:副） | 002 |
| mtGearboxTypCd | JSON(List) | 是  | - | 变速箱（001:手动、002:自动） | 001 |
| mtParkingRadarTypCd | JSON(List) | 是  | - | 前／后驻车雷达（001:前、002:后） | 001 |
| mtSeatHeatTypCd | JSON(List) | 否  | - | 	前后排座椅加热（001:前、002:后） | 002  |

### 交强险信息
| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| deathPayLimit | Number |是| 12(10,2)  | 死亡伤残赔偿限额 | 50000.01 |
| noResponDeathPayLimit | Number | 是  | 12(10.2)  | 无责任死亡伤残赔偿限额 | 50000.01 |
| noResponMedicalPayLimit | Number | 是  |  12(10.2) | 	无责任医疗费用赔偿限额 | 50000.01 |
| noResponPropertyLossPayLimit | Number | 是  | 12(10.2)  | 无责任财产损失赔偿限额 | 50000.01 |
| propertyLossPayLimit | Number | 是  | 12(10.2)  | 财产损失赔偿限额 | 50000.01 |
| medicalPayLimit | Number | 是  | 12(10.2)  | 	医疗费用赔偿限额 | 50000.01 |
| insuranceSum | Number | 是  | 12(10.2) | 	保险费合计(**上述六种赔偿限额之和**) | 300000.06 |
| rescueFundRate | Number | 否  |  3 | 救助基金占比(单位：% ，正数，最多保留两位小数，不得大于100) | 50 |
| rescueFund | Number | 否  | 12(10.2)  | 救助基金 | 50000.01 |
| dtInsuranceStart | Date | 是  | - | 保险期间-开始日期(不可以选择当前日期之后的日期) | 2017-01-01 00:00:00 |
| dtInsuranceEnd | Date | 是  | - | 保险期间-结束日期 | 2017-01-01 |
| mtInsuranceResolutionCd | JSON(List) | 是  | -  | 保险合同争议解决方式（001:协商、002:仲裁、003:诉讼） | 003 |
| hasInsurancePayHis | String | 是  | - | 是否有车险理赔记录（Y=是，N=否） | Y |
| engineNo | String | 是  | 30 | 发动机号 | 123456789987654321 |
| frameNo | String | 是  | 30 | 车架号 | WFIE231231 |
| plateNo | String | 是  | 20 | 车牌号码 | JWF1231233 |
| insurancePaySum | Number | 否  | 12(10,2) | 	客户车辆理赔总金额 | 50000.01 |
| accidentIllegalRate | Number | 否 | 3  | 与道路交通安全违法行为和道路交通事故相联系的浮动比率(单位：% ，正数，最多保留两位小数，不得大于100) | 50 |

### 代收车船费
| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| curYearUnpaid | Number |是| 12(10,2) | 当年应缴 | 200 |
| forfeit | Number |是| 12(10,2) | 滞纳金 | 200 |
| lastYearPaid | Number |是| 12(10,2) | 往年补缴 | 200 |
| feeSum | Number |是| 12(10,2) | 合计(计算公式=当年应缴+往年应缴+滞纳金) | 600 |
| paymentYear | Date |是| - | 缴费年份(不可以选择当前年之后的年份) | 2017 |

### 违章情况
| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| unclearedPenaltyPoints | Number |否| 3 | 	未清除违章扣分 | 2 |
| unpaidPenalty | Number |否|  12(10,2) | 未缴纳罚款金额 | 50000.01 |

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
    "appId": "2b79c4cfbde647749a639ccd355dffac", 
	"mtCollStyleCd": "DY", 
	"mtCollCatCd": "MV01", 
	"mtCollCd": "DY0601001", 
	"collValue": 123456.78, 
	"dtPurchased": "2017-05-03 00:00:00",
	"mortgageInfo": "这里是抵押摘要",
	"mtCollTypCd": "MV",
	"purchasedPrc": "1500000",
	"mvBasicInfo": {
		"approvedMass": "600", 
		"approvedPassenger": "4", 
		"brand": "奥迪", 
		"color": "褐色", 
		"drivenDistance": "223", 
		"dtFirstRecord": "2017-05-03 00:00:00",
		"engineCapacity": "2",  
		"isMadeInChina": "N", 
		"manufactured": "2017-05-03 00:00:00",
		"model": "进取型", 
		"mtFuelCd":[
			"002",
			"001"
		],
		"engineNo": "12233224234234", 
		"frameNo": "JJWEF1231231", 
		"plateNo": "DFSDF1231231", 
		"power": "700", 
		"priceMax": "500000", 
		"priceMin": "50000", 
		"series": "欧系", 
		"vehicleType": "小型汽车"
    },
	"mvConfInfo": {
		"mtAirconditionTypCd":[
			"002"
		],
		"mtCommonConfTypCd": [
			"002", 
			"001", 
			"003", 
			"004", 
			"005"
		],
		"mtDriverEleTypCd": [
			"001"
		],
		"mtGearboxTypCd": [
			"002"
		],
		"mtParkingRadarTypCd":[
			"001"
		],
		"mtSeatHeatTypCd": [
			"002"
		]
	},
 	"mvInsuranceInfo":{
		"accidentIllegalRate": "2", 
		"deathPayLimit": "200000", 
		"dtInsuranceEnd":  "2027-05-03 00:00:00",
		"dtInsuranceStart":  "2014-05-03 00:00:00",
		"hasInsurancePayHis": "N", 
		"insurancePaySum": "200000", 
		"insuranceSum": "4000000", 
		"medicalPayLimit": "2000000", 
		"mtInsuranceResolutionCd":[
			"001"
		],
		"noResponDeathPayLimit": "1000000", 
		"noResponMedicalPayLimit": "300000", 
		"noResponPropertyLossPayLimit": "100000", 
		"propertyLossPayLimit": "400000", 
		"rescueFund": "20000", 
		"rescueFundRate": "3"
	},
	"mvPaymentInfo":{
		"curYearUnpaid": "2000", 
		"feeSum": "200000", 
		"forfeit":  "2000",
		"lastYearPaid":  "5000",
		"paymentYear": "2017-05-03 00:00:00"
	},
	"mvPenaltyInfo": {
		"unclearedPenaltyPoints": "6", 
		"unpaidPenalty": "1200"
	},
    "collEvaluate": {
		"evaluateValue": 123456.78, 
		"dtEvaluated": "2017-05-03 00:00:00",
		"appraiser": "李四"
	},
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