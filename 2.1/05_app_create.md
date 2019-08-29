# 融资申请创建
## 描述
支持个人、企业融资申请创建。融资申请创建成功后，需要保存响应参数中的“申请ID”，作为后续交易的请求参数。

当借款人已存在一笔新建或审批中的申请时，再次创建新申请会不允许创建（以证件号和证件类型作为条件）。
## API代码
loan\_app:app:create

## 请求参数
借款人为个人时，需要提供：
    1. 个人借款人信息
        - 基本信息
        - 职业信息（非个体工商户/私营业主）
        - 经营信息（个体工商户/私营业主）
    2. 资金需求信息
    3. 担保信息（可录入多个，但至少有一个，无实物担保的情况需要填写信用或保证担保）
（个人借款人的联系人信息通过[借款人配偶信息](#借款人配偶信息)和[借款人亲朋信息](#借款人亲朋信息)接口提交）

借款人为企业时，需要提供：
    1. 企业借款人信息
    2. 联系人信息（可录入多个，但至少有一个）
    3. 资金需求信息
    4. 担保信息（可录入多个，但至少有一个，无实物担保的情况需要填写信用或保证担保）
具体定义如下：

| 名称 | 类型 | 是否必须 | 描述 | 
| --- | --- | --- | --- | 
| cp_cust | JSON |  | 企业借款人信息，与个人借款人信息同时只能存在一个，见[企业借款人信息](#企业借款人信息) |
| cs_cust | JSON |  | 个人借款人信息，与企业借款人信息同时只能存在一个，见[个人借款人信息](#个人借款人信息) |
| contacts | JSON(List) | 是 | 联系人信息（企业专用），见[联系人信息](#联系人信息（企业专用）) |
| fac | JSON | 是 | 资金需求信息 （企业、个人共用）， 见[资金需求信息](#资金需求信息) |
| col | JSON(List) | 是 | 担保信息 （企业、个人共用）， 见[担保信息](#担保信息) |
| callbackURL | String | 否 | 授信状态变更后通知回调URL( 如:http://api.xxxx.com/ljt/callback )，见[授信状态变更通知回调](#授信状态变更通知回调) |

### 企业借款人信息
| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| custId | String | 是 | 50 | 借款人在平台方的客户ID或编号，能够唯一标识某一客户 | 00927284 |
| nm | String | 是 | 80 | 企业名称(与营业执照上一致) | 北京某某公司 |
| bizRegNo | String | 是 | 18 | 营业执照号码 |  |
| idNo | String | 是 | 50 | 中征码／贷款卡 |  |
| isComb | String | 是 | 1 | 是否三证合一 |  |
| brandNm | String | 是 | 200 |  核心产品及品牌 |  |
| coreBiz | String | 是 | 255 | 主营业务 |  |
| isFreeTradeArea | String | 是 | 1 |  是否自贸易区 |  |
| mtCifCatCd | String | 是 | 20 |  控股经济分类与代码 |  |
| mtCityCd | String | 是 | 20 | 所在城市  |  |
| mtCorpSalutationCd | String | 是 | 20 | 公司类型 |  |
| mtIndDetailCd | String | 是 | 20 | 行业类型 |  |
| website | String | 是 | 50 | 网址 |  |
| dtRegistered | Date | 是 |  | 注册日期 |  | 
| incomeTaxNo | String | 是 | 20 | 地税登记号 |  | 
| nationalTaxNo | String | 是 | 20 | 国税登记号 |  | 
| registeredAddr | String | 是 | 20 | 注册地址 |  | 
| bizAddr | String | 是 | 50 | 经营地址 |  | 
| dtStart | Date | 是 |  | 开始营业日期 |  | 
| noOfBizSite | Number | 是 | 3 | 营业网点数量(单位/个) |  | 
| employeeCnt | Number | 是 | 30 (26,4)| 从业人数(单位/人) |  | 
| mtListedCd | String | 否 | 1 | 是否上市 |  | 
| paidUpCapital | Number | 是 | 30 (26,4) | 实收资本(单位/万元) |  | 
| authCapital | Number | 是 | 14 (12,2)| 注册资本(单位/万元) |  | 
| bizLandArea | Number | 否 | 8  | 经营场地面积(单位/平方米) |  | 
| mtBizLandOwnerCd | String | 是 | 20 | 经营场地所有权 |  | 
| saleAmt | Number | 是 | 14 (12,2)| 近一年销售额(单位/元) |  | 
| assetAmt | Number | 是 | 14 (12,2)| 资产价值(单位/元) |  | 
| ratal | Number | 是 | 14 (12,2)| 近一年纳税额(单位/元) |  | 
| socialSecurity | Number| 否 | 14 (12,2) | 近一年社保缴存额(单位/元) |  | 
| equityLine | Number | 否 | 14 (12,2)| 近一年公积金缴存额(单位/元) |  | 
| waterDosage | Number | 是 | 14 (12,2)| 近一年用水量(单位/吨) |  | 
| electricityDosage | Number | 是 | 14 (12,2)| 近一年用电量(单位/度) |  | 
| salaryTotal | Number | 否 | 14 (12,2)| 近一年发放工资(单位/元) |  | 
| mtSalaryTypCd | String | 否 | 1 | 工资发放方式|  | 
| principalNo | String | 是 | 20 | 经营电话/负责人电话 |  | 
| mtFinInsttnCd | String | 是 | 20 | 基本开户行 |  | 
| portrait | JSON | 否 | 1000 | 客户画像 | {"行业地位":"市场占有率第一"}|
| bizCertificates | JSON(List) | 否 |  | 见[经营许可证信息](###经营许可证信息) ||


### 经营许可证信息
经营许可证信息由三部分组成：经营许可证编号、经营许可证类型、经营许可证到期日

| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| no | String | 是 | 16 | 经营许可证编号 |  |
| mtBizCertificateTypCd | String | 是 | 2 | 经营许可证类型 |  |
| dtExpiry | Date | 是 |  | 经营许可证到期日 |  |

### 个人借款人信息
个人借款人信息由三部分组成：

| 名称 | 类型 | 是否必须 | 描述 | 备注 |
| --- | --- | --- | --- | --- |
| base | JSON | 是 | [基本信息](#基本信息) | |
| employ | JSON | 否 | [职业信息](#职业信息) | 基本信息中“是否为个体工商户/私营业主”为否时必须填写 | 
| business | JSON | 否 | [经营信息](#职业信息) | 基本信息中“是否为个体工商户/私营业主”为是时必须填写 | 

#### 基本信息
| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| custId | String | 是 | 50 | 借款人在平台方的客户ID或编号，能够唯一标识某一客户 | 0092728480d24f5d8 |
| nm | String | 是 | 80 | 借款人姓名（与身份证上相同） | 张三 |
| idNo | String | 是 | 50 | 身份证号码 |  |
| dtIssued | Date | 否 |  | 身份证签发日期 |  |
| dtExpiry | Date | 否 |  | 身份证到期日（长期身份证可以为空） |  |
| mtGenderCd | String | 是 | 20 | 性别 |  |
| mtMaritalStsCd | String | 是 | 20 | 婚姻情况 |  |
| mtEduLvlCd | String | 是 | 20 | 最高学历 |  |
| mtResidenceStsCd | String | 是 | 20 | 本地居住情况 |  |
| isFamily | String | 是 | 1 | 是否自有房产 |  |
| mtJobSectorCd | String | 是 | 20 | 职业 |  |
| yearIncAmt | String | 否 | 14 (12,2)| 近1年税后收入(单位/元) |  |
| email | String | 否 | 30 |电子邮箱 |  |
| mtCityCd | String | 是 | 20 | 所在城市 |  |
| mobileNo | String | 是 | 11 | 手机号 |  |
| mtIndvMobileUsageStsCd | String | 否 | 20 |  手机使用年限 |  |
| qq | Number | 否 |  15 | QQ号 |  |
| weChat | String | 否 |  50 | 微信号 |  |
| bankCard | Number | 是 |  14 (12,2)| 近一年银行卡流水总额 |  |
| creditCardLines | Number | 否 |  14 (12,2)| 信用卡额度 |  |
| loanFixedYear | Number | 否 |  20 | 贷款记录年限 |  |
| isBizEntity | String | 是 | 1 | 是否个体工商户／私营业主 |  | 
| portrait | JSON | 否 | 1000 | 客户画像 | {"芝麻评分":"698"}|
| repaymentCard | String | 否 | 30 | 还款银行卡号 | 622649671749152511 ||

#### 职业信息
“是否为个体工商户/私营业主”为 "否" 时必须输入：

| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| employerNm | String | 是 |  80 | 工作单位 |  |
| mtPosHeldCd | String | 是 |  20 | 职位|  |
| prevServiceYr | Number | 否 |  60 | 工作年限(年)|  |
| prevServiceMth | Number | 否 |  12 | 工作年限(月)|  |
| dtWorkInCurrIndustry | Date | 否 |   | 从事现行业时间 |  ||

####  经营信息
“是否为个体工商户/私营业主”为“是”时必须输入：

| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| isLegalRep | String | 是 |  1 | 是否法定代表人  |  |
| mtIndDetailCd | String | 是 |  50 | 行业类型 |  |
| bizRegNo | String | 是 |  18 | 营业执照号 |  |
| bizAddr | String | 是 |  50 | 经营地址 |  |
| bizArea | String | 是 |  255 | 经营范围 |  |
| currentTotal | Number | 是 |  14 (12,2) | 近一年流水总额（单位：元） |  |
| waterDosage | Number | 是 |  14 (12,2)| 近一年用水量（单位：吨） |  |
| electricityDosage | Number | 是 |  14 (12,2)| 近一年用电量（单位：度） |  |
| ratal | Number | 是 |  14 (12,2)| 近一年纳税额（单位：元） |  |
| socialSecurity | Number | 否 |  14 (12,2)| 近一年社保缴存额 （单位：元） |  |
| equityLine | Number | 否 |  14 (12,2)| 近一年公积金缴存额 （单位：元） |  |
| employees | Number | 否 |  12 | 员工人数 |  |
| salaryTotal | Number | 否 |  14 (12,2)| 近一年发放工资 （单位：元） |  ||


###  联系人信息（企业专用）

| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| nm | String | 是 | 80 | 联系人姓名 | |
| mobileNo | String | 是 | 11 | 联系人手机号 | |
| mtCifContactCd | String | 是 | 20 | 与客户关系，借款人为个人时必需 | |
| mtPosHeldCd | String | 是 | 20 | 职位，借款人为企业时必需 | |
| email | String | 否 | 50 | 联系人邮箱 | ||


### 资金需求信息

| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| mtFacCd | String | 是 | 20 | 业务类型 |  |
| lmtAppr | Number | 是 | 14 (12,2)| 申请额度 |  |
| dtMaturity | Date | 否 |  | 到期日 |  |
| tenureAppr | Number | 是 | 6 | 业务期限 |  |
| mtTimeCd | String | 是 | 1| 业务期限类型 | D-天、M-月、Y-年 |
| mtRepymtTypCd | String | 是 | 20 | 偿还方式 |  |
| isRevolvingAllowed | String | 是 | 1 | 授信额度是否可循环，默认为否 | Y/N |
| mtFacPurCds | JSON | 是 | 100 | 资金用途，可输入多个 |  |
| intRate | Number | 是 | 6 (2,4)| 年化利率 |  |
| intRateInSuspense | Number | 否 | 6 (2,4)| 罚息利率 |  ||

### 担保信息


| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| mtCollStyleCd | String | 是 | 20 | 担保方式 | BZ-保证;DY-抵押;ZY-质押;XY-信用 |
| mtCollTypCd | String | 是 | 20 | 担保类型 |  |
| mtCollCatCd | String | 是 | 20 | 担保品种 |  |
| mtCollCd | String | 是 | 20 | 担保小类 |  |
| collValue | Number | 是 | 20(18,2) | 担保品价值 |  |
| isDeposit | String | 是 | 1 | 是否保证金 | Y/N |
| collOwner | String | 否 | 50 | 担保品所有者名称 |    |
- 信用担保品示例
```javascript
{
    "col": [
        {
            "collOwner": "张三",//一般为借款人姓名
            "collValue": "30000000", //与申请额度相等
            "isDeposit": "N",//固定值
            "mtCollCatCd": "OA01",//信用担保品时，固定值
            "mtCollCd": "XY0101001",//信用担保品时，固定值
            "mtCollStyleCd": "XY",//信用担保品时，固定值
            "mtCollTypCd": "OA"//信用担保品时，固定值
        }
    ]
}
```



## 响应参数
| 名称 | 类型 | 描述 |示例值 |
| --- | --- | --- | --- |
| app_id | String | 申请ID | 0092728480d24f5d87bf63639b5cfe1c |

## 错误码
| 描述 | HTTP状态码 | 语义 |
| --- | --- | --- | 
| app_id未找到 | 400 | 请输入正确的app_id,或检查申请类型与申请ID是否匹配 |
| 存在在途申请 | 405 | 客户的前一笔融资请求尚未批准或取消，无法再次发起新融资申请 |
## 示例
### 请求示例（企业）
```javascript
{
    "col": [
        {
            "collOwner": "所有人", 
            "collValue": "111111",
            "mtCollStyleCd": "ZY", 
            "mtCollTypCd": "DP",
			"mtCollCatCd": "DP01",
			"mtCollCd": "ZY0101001"
        }
    ], 
    "contacts": [
        {
            "email": "1233@qq.com", 
            "mobileNo": "13333333333", 
            "mtCifContactCd": "F001", 
            "mtPosHeldCd": "001", 
            "nm": "联系人"
        }
    ], 
    "cp_cust": {
        "assetAmt": 55, 
        "authCapital": 5456, 
        "bizAddr": "北京", 
        "bizLandArea": 4576, 
        "bizRegNo": "58da894a6fc84fb", 
        "brandNm": "213123412", 
        "coreBiz": "手机", 
        "custId": "2f50c12b0d064157bf", 
        "dtRegistered": "2017-05-03 15:12:24", 
        "dtStart": "2017-05-03 15:12:24", 
        "electricityDosage": 879, 
        "employeeCnt": 12333445, 
        "equityLine": 879, 
        "idNo": "a2ebc531112b4fa08d", 
        "incomeTaxNo": "ds13wqe5", 
        "isComb": "Y", 
        "isFreeTradeArea": "Y", 
        "mtBizLandOwnerCd": "2", 
        "mtCifCatCd": "112", 
        "mtCityCd": "110100", 
        "mtCorpSalutationCd": "2", 
        "mtFinInsttnCd": "02", 
        "mtIndDetailCd": "a0111", 
        "mtListedCd": "Y", 
        "mtSalaryTypCd": "3", 
        "nationalTaxNo": "1332", 
        "nm": "企业", 
        "noOfBizSite": 333, 
        "paidUpCapital": 676, 
        "principalNo": "53453", 
        "ratal": 3, 
        "registeredAddr": "北京", 
        "salaryTotal": 879, 
        "saleAmt": 33, 
        "socialSecurity": 879, 
        "waterDosage": 879, 
        "website": "baidu.com",
        "portrait": "{\"企业实力\":\"世界500强\"}",
		"bizCertificateList":[
			{
				"dtExpiry":"2017-05-16 7:18:12",
				"no":"b4812a23a4c14d0ea659",
				"mtBizCertificateTypCd":"00"
			}
		]
    }, 
    "fac": {
        "dtMaturity": "2017-05-03 15:12:24", 
        "intRate": 123, 
        "isRevolvingAllowed": "Y", 
        "lmtAppr": 123, 
        "mtFacCd": "P1011", 
        "mtFacPurCds": [
            "1001", 
            "1002"
        ], 
        "mtRepymtTypCd": "001", 
        "mtTimeCd": "D", 
        "tenureAppr": "12"
    }
}
```

### 请求示例（个人）
#### 个人非私营业主
```javascript
{
    "col": [
        {
            "collOwner": "所有人", 
            "collValue": "111111",
            "mtCollStyleCd": "ZY", 
            "mtCollTypCd": "DP",
			"mtCollCatCd": "DP01",
			"mtCollCd": "ZY0101001"
        }
    ],
    "cs_cust": {
        "base": {
            "bankCard": 1234556565, 
            "creditCardLines": 12345, 
            "custId": "77f392388c2e410684", 
            "dtExpiry": "2017-05-03 15:12:27", 
            "dtIssue": "2017-05-03 15:12:27", 
            "email": "123@qq.com", 
            "idNo": "1867fc918fdc4e349e", 
            "isBizEntity": "N", 
            "isFamily": "Y", 
            "loanFixedYear": 11, 
            "mobileNo": "18888888888", 
            "yearIncAmt": 100000, 
            "mtCityCd": "110100", 
            "mtEduLvlCd": "01", 
            "mtGenderCd": "M", 
            "mtIndvMobileUsageStsCd": "01", 
            "mtJobSectorCd": "10000", 
            "mtMaritalStsCd": "02", 
            "mtResidenceStsCd": "01", 
            "nm": "个人非私营", 
            "qq": 12345, 
            "weChat": "1234",
            "portrait": "{\"芝麻信用分\":\"750\"}"
        }, 
        "employ": {
            "dtWorkInCurrIndustry": "2017-05-03 15:12:27", 
            "employerNm": "单位姓名", 
            "mtPosHeldCd": "001", 
            "prevServiceMth": 1, 
            "prevServiceYr": 2
        }
    }, 
    "fac": {
        "dtMaturity": "2017-05-03 15:12:27", 
        "intRate": 123, 
        "isRevolvingAllowed": "Y", 
        "lmtAppr": 123, 
        "mtFacCd": "P1011", 
        "mtFacPurCds": [
            "1001", 
            "1002"
        ], 
        "mtRepymtTypCd": "001", 
        "mtTimeCd": "D", 
        "tenureAppr": "12"
    }
}
```
#### 个人私营业主
```javascript
{
    "col": [
        {
            "collOwner": "所有人", 
            "collValue": "111111",
            "mtCollStyleCd": "ZY", 
            "mtCollTypCd": "DP",
			"mtCollCatCd": "DP01",
			"mtCollCd": "ZY0101001"
        }
    ],
    "cs_cust": {
        "base": {
            "bankCard": 1234556565, 
            "creditCardLines": 12345, 
            "custId": "0bbe35b8858345d19a", 
            "dtExpiry": "2017-05-03 15:12:25", 
            "dtIssue": "2017-05-03 15:12:25", 
            "email": "123@qq.com", 
            "idNo": "5cb86df87c874f9585", 
            "isBizEntity": "Y", 
            "isFamily": "Y", 
            "loanFixedYear": 11, 
            "mobileNo": "18888888888", 
            "yearIncAmt": 100000, 
            "mtCityCd": "110100", 
            "mtEduLvlCd": "01", 
            "mtGenderCd": "M", 
            "mtIndvMobileUsageStsCd": "01", 
            "mtJobSectorCd": "10000", 
            "mtMaritalStsCd": "02", 
            "mtResidenceStsCd": "01", 
            "nm": "个人私营", 
            "qq": 12345, 
            "weChat": "1234",
            "portrait": "{\"芝麻信用分\":\"750\"}"
        }, 
        "business": {
            "bizAddr": "北京", 
            "bizArea": "电子商务", 
            "bizRegNo": "d67402dae31b481", 
            "currentTotal": 123, 
            "electricityDosage": 123, 
            "employees": "22", 
            "equityLine": 123, 
            "isLegalRep": "Y", 
            "mtIndDetailCd": "a0111", 
            "mtJobSectorCd": "10000", 
            "ratal": 123, 
            "salaryTotal": 123, 
            "socialSecurity": 123, 
            "waterDosage": 123
        }
    }, 
    "fac": {
        "dtMaturity": "2017-05-03 15:12:25", 
        "intRate": 123, 
        "isRevolvingAllowed": "Y", 
        "lmtAppr": 123, 
        "mtFacCd": "P1011", 
        "mtFacPurCds": [
            "1001", 
            "1002"
        ], 
        "mtRepymtTypCd": "001", 
        "mtTimeCd": "D", 
        "tenureAppr": "12"
    }
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