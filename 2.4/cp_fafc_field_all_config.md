# 企贷申请创建
## 描述
支持企业申请创建。申请创建成功后，需要保存响应参数中的“申请ID”，作为后续交易的请求参数。

## API代码
loan_app:cp_app:create

## 请求参数
借款人为企业时，需要提供：
    1. 企业信息
    2. 经营信息
    3. 关联人信息(有且只有一个)
    4. 联系人信息（可录入多个，但至少有一个）
    5. 业务信息
    6. 担保信息（可录入多个，但至少有一个，无实物担保的情况需要填写信用或保证担保）
    7. 申请材料信息
具体定义如下：

| 名称 | 类型 | 是否必须 | 描述 | 
| --- | --- | --- | --- | 
| cif | JSON | 是 | 企业信息 见[企业信息](#企业信息) |
| biz | JSON | 是 | 经营信息 见[经营信息](#企业经营信息) |
| rels | JSON | 是 | 主要成员 见[主要成员](#企业主要成员) |
| contact | JSON(List) | 是 | 联系人信息，见[联系人信息](#企业联系人信息) |
| fac | JSON | 是 | 业务信息， 见[业务信息](#企业业务信息) |
| doc | JSON | 是 | 申请材料信息， 见[申请材料](#企业申请材料) |

### 企业信息
企业借款人信息由三部分组成

| 名称 | 类型 | 是否必须 | 描述 | 
| --- | --- | --- | --- | 
| corporate | JSON | 是 | 客户信息 见[客户信息](#客户信息) |
| taxInfo | JSON | 是 | 工商税务信息 见[工商税务信息](#工商税务信息) |
| bizCertificates | JSON | 是 | 经营许可证信息 见[经营许可证信息](#经营许可证信息) |

### 客户信息
| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| nm | String | 是 | 300 | 企业名称(与营业执照上一致) | 北京某某公司 |
| isComb | String | 是 | 1 | 是否三证合一 |  |
| idNo | String | 是 | 50 | 统一社会信用代码(是否多证合一为是) |  |
| idNo | String | 是 | 50 | 营业执照号码(是否多证合一为否) |  |
| mtCtryCd | String | 是 | 20 | 所在城市(国家)  |  |
| mtStateCd | String | 是 | 20 | 所在城市(省份)  |  |
| mtCityCd | String | 是 | 20 | 所在城市(区域)  |  |
| mtCorpSalutationCd | String | 是 | 20 | 公司类型 |  |
| principalNo | String | 是 | 20 | 联系电话 |  |
| mtListedCd | String | 否 | 20 | 是否上市 |  | 
| stockCode | String | 否 | 20 | 股票代码 |  |
| coreBiz | String | 是 | 255 | 主营业务 |  |
| brandNm | String | 是 | 200 |  核心产品及品牌 |  |
| mtCifCatCd | String | 是 | 200 |  资本金来源 |  |
| mtFinInsttnCd | String | 是 | 20 | 基本开户行 |  | 
| nationalityMtCtryCd | String | 是 | 20 | 注册国家 |  |
| grpNm | String | 是 | 100 | 集团名称 |  |
| isFreeTradeArea | String | 是 | 1 |  是否自贸区 |  |
| mtIndCatCd | String | 是 | 20 | 行业类型(大类) |  |
| mtIndCd | String | 是 | 20 | 行业类型(中类) |  |
| mtIndDetailCd | String | 是 | 20 | 行业类型(小类) |  |
| website | String | 是 | 50 | 网址 |  |

### 工商税务信息
| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| dtRegistered | Date | 是 |  | 注册日期 |  | 
| authCapital | Number | 是 | 30 (26,4)| 注册资本(单位/万元) |  |
| registeredAddr | String | 是 | 20 | 注册地址 |  | 
| bizRegDtExpiry | String | 是 | 20 | 营业执照到期日 |  |
| bizRegNo | String | 是 | 20 | 中征码 |  |

### 经营许可证信息

| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| no | String | 是 | 50 | 经营许可证编号 |  |
| mtBizCertificateTypCd | String | 是 | 2 | 经营许可证类型 |  |
| dtExpiry | Date | 是 |  | 经营许可证到期日 |  |

### 企业经营信息
企业经营信息由以下信息组成

| 名称 | 类型 | 是否必须 | 描述 | 
| --- | --- | --- | --- | 
| businessInfo | JSON | 是 | 经营信息 见[经营信息](#经营信息) |

### 经营信息
| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| dtCommenceTrading | date | 是 | 50 | 开始营业日期 |  | 
| bizAddr | String | 是 | 50 | 经营地址 |  | 
| saleAmt | Number | 是 | 30 (26,4)| 近一年销售额(单位/元) |  |
| ratal | Number | 是 | 14 (12,2)| 近一年纳税额(单位/元) |  |
| employeeCnt | String | 是 | 30| 员工数 |  |
| assetAmt | Number | 是 | 30 (26,4)| 资产价值(单位/元) |  |
| mtBizLandOwnerCd | String | 是 | 20 | 经营场地所有权 |  |
| bizLandArea | Number | 否 | 8  | 经营场地面积(单位/平方米) |  |
| waterDosage | Number | 是 | 14 (12,2)| 近一年用水量(单位/吨) |  |
| electricityDosage | Number | 是 | 14 (12,2)| 近一年用电量(单位/度) |  |
| salaryTotal | Number | 否 | 14 (12,2)| 近一年发放工资(单位/元) |  |
| mtSalaryTypCd | String | 否 | 1 | 工资发放方式|  |
| socialSecurity | Number (12,2)| 否 | 14 | 近一年社保缴存额(单位/元) |  | 
| equityLine | Number | 否 | 14 (12,2)| 近一年公积金缴存额(单位/元) |  | 
| noOfBizSite | Number | 是 | 3 | 营业网点数量(单位/个) |  |


### 企业主要成员
企业主要成员信息由以下信息组成

| 名称 | 类型 | 是否必须 | 描述 | 
| --- | --- | --- | --- | 
| relInfo | JSON | 是 | 关联信息 见[关联信息](#关联信息) |
| identity | JSON | 是 | 身份信息 见[身份信息](#身份信息) |
| finance | JSON | 是 | 财务信息 见[财务信息](#财务信息) |
| emplymt | JSON | 是 | [职业信息-非私营业主](#职业信息-非私营业主) or [职业信息-私营业主](#职业信息-私营业主) | |

### 关联信息



#### 身份信息
| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| nm | String | 是 | 300 | 借款人姓名（与身份证上相同） | 张三 |
| idNo | String | 是 | 50 | 身份证号码 |  |
| mtCifIdTypCd | String | 是 | 20 | 证件类型 |  |
| nationalityMtCtryCd | String | 是 | 20 | 国籍 |  |
| mtCityCd | String | 是 | 20 | 现常住地（市） |  |
| mtCtryCd | String | 是 | 20 | 现常住地（国家） |  |
| mtStateCd | String | 是 | 20 | 现常住地（省） |  |
| dtIssue | Date | 否 |  | 身份证签发日期 时间格式：yyyy-MM-dd HH:mm:ss|  |
| dtExpiry | Date | 否 |  | 身份证到期日（长期身份证可以为空） |  |
| dtRegistered | Date | 否 |  | 出生日期 |  |
/ isLongEffec | String | 否 |  | 证件到期日 是否长期有效 Y 或 N  |  |
| mtGenderCd | String | 否 | 20 | 性别 |  |
| mtMaritalStsCd | String | 否 | 20 | 婚姻情况 |  |
| mtEduLvlCd | String | 否 | 20 | 最高学历 |  |
| mtResidenceStsCd | String | 否 | 20 | 本地居住情况 |  |
| mobileNo | String | 否 | 20 | 手机号 |  |
| mtIndvMobileUsageStsCd | String | 否 | 20 |  手机使用年限 |  |
| email | String | 否 | 100 |电子邮箱 |  |
| qq | Number | 否 |  15 | QQ号 |  |
| weChat | String | 否 |  50 | 微信号 |  |

#### 财务信息
| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| yearIncAmt | String | 否 | 30 (26,4)| 近1年税后收入(单位/元) |  |
| isFamily | String | 否 | 1 | 是否自有房产 |  |
| hasCar | String | 否 | 1 | 是否有车 |  |
| plateNo | String | 否 | 1 | 车牌号码 |  |
| hasCreditCard | String | 否 | 1 | 是否有信用卡 |  |
| creditCardLines | Number | 否 |  14 (12,2)| 信用卡额度 |  | 

“是否为个体工商户/私营业主”为 "否" 时必须输入：

#### 职业信息-非私营业主
| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| isBizEntity | String | 是 | 1 | 是否个体工商户/私营业主 |  示例:Y/N |
| employerNm | String | 否 |  100 | 工作单位 |  |
| mtJobSectorCd | String | 否 | 20 | 职业 |  |
| prevServiceYr | Number | 否 |  60 | 工作年限(年)|  |
| prevServiceMth | Number | 否 |  12 | 工作年限(月)|  |
| mtPosHeldCd | String | 否 |  20 | 职位|  |
| employerPhone | String | 否 |  20 | 单位电话|  |
| dtWorkInCurrIndustry | Date | 否 |   | 从事现行业时间 时间格式：yyyy-MM-dd |  ||

#### 职业信息-私营业主
“是否为个体工商户/私营业主”为“是”时必须输入：

| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| isComb | String | 否 |  1 | 是否多证合一  |  Y 或 N |
| bizRegNo | String | 否 |  50 | 营业执照号 或者 统一社会信用代码 |  |
| bizAddr | String | 否 |  50 | 经营地址 |  |
| bizRegDtExpiry | Date | 否 |  10 | 营业执照到期日 | 时间格式：yyyy-MM-dd |
| isBussLongEffec | String | 否 |  1 | 营业执照到期日是否长期 | 如果是，则不需要传入营业执照到期日 值：Y 或 N" /
| isLegalRep | String | 否 |  1 | 是否法定代表人  |  |
| currentTotal | Number | 否 |  20 (18,2) | 近一年流水总额（单位：元） |  |
| yearSaleMarginsRate | Number | 否 |  20 (18,2) | 销售毛利润率 |  |
| ratal | Number | 否 |  14 (12,2)| 近一年纳税额（单位：元） |  |
| electricityDosage | Number | 否 |  14 (12,2)| 近一年用电量（单位：度） |  |
| waterDosage | Number | 否 |  14 (12,2)| 近一年用水量（单位：吨） |  |
| socialSecurity | Number | 否 |  14 (12,2)| 近一年社保缴存额 （单位：元） |  |
| equityLine | Number | 否 |  14 (12,2)| 近一年公积金缴存额 （单位：元） |  |
| employees | Number | 否 |  14 (12,2)| 员工人数 |  |
| salaryTotal | Number | 否 |  14 (12,2)| 近一年发放工资 （单位：元） |  |
| workPhone | String | 否 |  14 (12,2)| 联系电话 |  |
| mtIndDetailCd | String | 否 |  20 | 行业类型 |  |
| bizArea | String | 否 |  255 | 经营范围 |  ||

### 企业联系人信息
| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| nm | String | 是 | 100 | 联系人姓名 | |
| mobileNo | String | 是 | 20 | 联系人手机号 | |
| mtCifContactCd | String | 是 | 20 | 与客户关系，借款人为个人时必需 | |
| mtPosHeldCd | String | 是 | 20 | 职位，借款人为企业时必需 | |
| email | String | 否 | 50 | 联系人邮箱 | ||


### 企业业务信息

| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| mtFacCd | String | 是 | 20 | 业务类型 |  |
| lmtAppr | Number | 是 | 30 (26,4)| 申请额度 |  |
| dtMaturity | Date | 否 |  | 到期日 |  |
| tenureAppr | Number | 是 | 6 | 业务期限 |  |
| mtTimeCd | String | 是 | 1| 业务期限类型 | D-天、M-月、Y-年 |
| mtRepymtTypCd | String | 是 | 20 | 偿还方式 |  |
| isRevolvingAllowed | String | 是 | 1 | 授信额度是否可循环，默认为否 | Y/N |
| mtFacPurCds | JSON | 是 | 100 | 资金用途，可输入多个 |  |
| intRate | Number | 是 | 9 (5,4)| 年化利率 |  |
| intRateInSuspense | Number | 否 | 9 (5,4)| 罚息利率 |  ||

### 申请材料
| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| url | Json | 是 |  | oss上传密钥 [oss上传密钥](#oss上传密钥) |  |
| docs | Json(list) | 是 |  | 申请材料列表 [业务上传申请材料列表](#业务上传申请材料列表) |  |


#### oss上传密钥
| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| accessid | String | 是 | 20 |  |  |
| policy | String | 是 | 20 |  |  |
| signature | String | 是 | 20 |  |  |
| dir | String | 是 | 20 |  |  |
| host | String | 是 | 20 |  |  |
| callback | String | 是 | 20 |  |  |

#### 业务上传申请材料列表 
| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| mtDocTypeCd | String | 是 | 20 | 申请材料门类Cd |  |
| mtDocCd | String | 是 | 20 |  | 申请材料Cd，在上传申请材料的时候需要使用 |
| mtDocCdDscp | String | 是 | 20 | 申请材料描述 |  |
| mtDocCatCd | String | 是 | 20 | 申请材料大类Cd |  |
| refId | String | 是 | 20 |  | 申请材料关联ID，在上传申请材料的时候需要使用 |
| required | String | 是 | 20 |  是否必须，Y是，N不是 |  |

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