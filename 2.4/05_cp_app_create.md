# 企贷申请创建
## 描述
支持企业申请创建。申请创建成功后，需要保存响应参数中的“申请ID”，作为后续交易的请求参数。

## API代码
loan_app:cp_app:create

## 请求参数
借款人为企业时，需要提供：
    1. 企业信息 
    2. 经营信息 
    3. 企业财报信息(非必选)
    4. 关联人信息(有且只有一个)
    5. 联系人信息（可录入多个，但至少有一个）
    6. 业务信息
    7. 定性打分信息
    8. 申请材料信息
具体定义如下：

| 名称 | 类型 | 是否必须 | 描述 | 
| --- | --- | --- | --- | 
| cif | JSON | 是 | 企业信息 见[企业信息](#企业信息) |
| biz | JSON | 是 | 经营信息 见[经营信息](#企业经营信息) |
| fin | JSON | 是 | 企业财报 见[企业财报](#企业财报信息) |
| rels | JSON | 是 | 主要成员 见[主要成员](#企业主要成员) |
| contact | JSON(List) | 是 | 联系人信息，见[联系人信息](#企业联系人信息) |
| fac | JSON | 是 | 业务信息 见[业务信息](#企业业务信息) |
| doc | JSON | 是 | 申请材料信息 见[申请材料](#企业申请材料) |
| ccms | JSON | 是 | 定性打分 见[定性打分](#定性打分信息) |
| callbackURL | String | 否 | 授信状态变更后通知回调URL( 如:http://api.xxxx.com/ljt/callback )，见[授信状态变更通知回调](/2.1/07_app_sts_call_back.md) |

### 企业信息
企业借款人信息由四部分组成

| 名称 | 类型 | 是否必须 | 描述 | 
| --- | --- | --- | --- | 
| corporate | JSON | 是 | 客户信息 |
| taxInfo | JSON | 是 | 工商税务信息|
| bizCertificates | JSON（list） | 是 | 经营许可证信息 |
| feature | JSON | 是 | 特色信息 |

### 企业经营信息
企业经营信息由以下信息组成

| 名称 | 类型 | 是否必须 | 描述 | 
| --- | --- | --- | --- | 
| biz | JSON | 是 | 经营信息 |


### 企业财报信息
企业财报信息由以下信息组成

| 名称 | 类型 | 是否必须 | 描述 | 
| --- | --- | --- | --- | 
| fin | JSON | 是 | 企业财报 |


### 企业主要成员
企业主要成员信息由以下信息组成

| 名称 | 类型 | 是否必须 | 描述 | 
| --- | --- | --- | --- | 
| legalRelInfo | JSON | 是 | 关联信息|
| identity | JSON | 是 | 身份信息|
| finance | JSON | 是 | 财务信息|
| emplymt | JSON | 是 | 经营/职业信息|


### 企业联系人信息
| 名称 | 类型 | 是否必须 | 描述 | 
| --- | --- | --- | --- | 
| contact | JSON(list) | 是 | 联系人信息 |

### 企业业务信息
| 名称 | 类型 | 是否必须 | 描述 | 
| --- | --- | --- | --- | 
| fac | JSON | 是 | 业务信息 |

### 申请材料
| 名称 | 类型 | 是否必须  | 描述 | 示例值 |
| --- | --- | --- | ---  | --- |
| cifDocRefId | string |  | 上传的申请材料的关联CIF的Id,此Id从获取产品配置接口中返回的refId |  |
| facDocRefId | string |  | 上传的申请材料的关联FAC的Id,此Id从获取产品配置接口中返回的refId  |  |


#### oss上传密钥
| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| accessid | String | 是 | 20 |  |  |
| policy | String | 是 | 20 |  |  |
| signature | String | 是 | 20 |  |  |
| dir | String | 是 | 20 |  |  |
| host | String | 是 | 20 |  |  |
| callback | String | 是 | 20 |  |  |

### 定性打分信息
| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| mtCpCreditModelCd | String | 是 |  | 企业指标模型cd |  |
| options | JSON(list) | 是 |  | 企业指标模型选项 |  |

## 响应参数
| 名称 | 类型 | 描述 |示例值 |
| --- | --- | --- | --- |
| app_id | String | 申请ID | 0092728480d24f5d87bf63639b5cfe1c |

## 错误码
| 描述 | HTTP状态码 | 语义 |
| --- | --- | --- | 
| app_id未找到 | 400 | 请输入正确的app_id,或检查申请类型与申请ID是否匹配 |
| 存在在途申请 | 405 | 客户的前一笔融资请求尚未批准或取消，无法再次发起新融资申请 |


### 请求示例

{
	"cif": {
		"corporate": {
			"mtCifCatCd": "111",
			"mtCorpSalutationCd": "1",
			"mtFinInsttnCd": "01",
			"nationalityMtCtryCd": "CN",
			"mtIndCd": "c305",
			"isComb": "N",
			"mtListedCd": "N",
			"isFreeTradeArea": "Y",
			"mtIndDetailCdDscp": "玻璃包装容器制造",
			"nationalityMtCtryCdDscp": "中国",
			"cancelledNum": 0,
			"approvedNum": 0,
			"toTenantId": null,
			"toTenantIdDscp": null,
			"fromTenantId": null,
			"fromTenantIdDscp": null,
			"nm": "测试借款企业",
			"idNo": "370973044645697719",
			"mtCifIdTypCd": "C2",
			"mtCifIdTypCdDscp": "营业执照注册号",
			"mtCifIdTypCdOld": "C2",
			"mtCorpSalutationCdDscp": "企业法人",
			"coreBiz": "测试",
			"principalNo": "136677889",
			"mtCtryCd": "CN",
			"mtCtryCdDscp": "中国",
			"mtStateCd": "110000",
			"mtStateCdDscp": "北京市",
			"mtCityCd": "110100",
			"mtCityCdDscp": "市辖区(北京市)",
			"mtCifCatCdDscp": "国有绝对控股",
			"brandNm": "12",
			"grpNm": "12121212121",
			"website": "www.baidu.com",
			"mtIndCatCd": "c30",
			"mtIndCatCdDscp": "非金属矿物制品业",
			"mtIndDetailCd": "c3055",
			"mtIndCdDscp": "玻璃制品制造",
			"mtIndTypCd": "c",
			"mtIndTypCdDscp": "制造业",
			"mtFinInsttnCdDscp": "中国工商银行",
			"updatedBy": "044e4e60e38448ad91c83fcc51af168a",
			"dtUpdated": "2018-10-27 00:00:00",
			"riskTipsNum": null,
			"legalPerson": null,
			"stockCode": null,
			"mtListedCdDscp": null,
			"locateAddr": null,
			"loanStyleChangeFlag": null
		},
		"taxInfo": {
			"dtRegistered": "2018-10-26 00:00:00",
			"isLongEffec": true,
			"bizRegDtExpiry": "",
			"bizRegNo": "132312312312978790",
			"authCapital": "12",
			"registeredAddr": "12",
			"isBussLongEffec": "Y",
			"incomeTaxNo": "00000000",
			"nationalTaxNo": "88888888",
			"corpIdNo": "3212313215468798",
			"bizCertificates": null,
			"uniformSocialCreditCode": null,
			"businessLicenseRegistrationNumber": "132312312312978790",
			"loanStyleChangeFlag": null
		},
		"bizCertificates": [{
				"mtBizCertificateTypCd": "00",
				"no": "123213213213",
				"dtExpiry": "2020-07-14 00:00:00"
			},
			{
				"mtBizCertificateTypCd": "00",
				"no": "888888888888888",
				"dtExpiry": "2020-07-14 00:00:00"
			}
		]
	},
	"biz": {
		"cdtFileId": null,
		"employeeCnt": "1",
		"assetAmt": "1",
		"noOfBizSite": 1,
		"mtCorpTypeCd": "04",
		"mtCorpTypeCdDscp": "微",
		"dtCommenceTrading": "2018-10-30 00:00:00",
		"bizAddr": "1",
		"mtBizLandOwnerCd": "1",
		"mtBizLandOwnerCdDscp": "自有",
		"bizLandArea": 1,
		"saleAmt": "1",
		"ratal": "1",
		"waterDosage": "1",
		"electricityDosage": "1",
		"salaryTotal": "1",
		"mtSalaryTypCd": "1",
		"mtSalaryTypCdDscp": "打卡",
		"socialSecurity": "1",
		"equityLine": "1",
		"loanStyleChangeFlag": null
	},
	"rel": {
		"mtCifRelCd": "CI003",
		"legalRelInfo": {
			"isActualCtrl": "Y",
			"isInvolvedMgmt": "Y",
			"dtInCompSince": "2016-06-07 00:00:00",
			"dtInBizLineSince": "2016-06-01 00:00:00",
			"mgmtExperience": "测试经理",
			"mtPosHeldCd": "001"
		},
		"identity": {
			"mtCifIdTypCd": "I2",
			"idNo": "5465641235661157",
			"isLongEffec": "N",
			"dtExpiry": "",
			"nationalityMtCtryCd": "CN",
			"nationalityMtCtryCdDscp": "中国",
			"nm": "测试关联人",
			"mtGenderCd": "M",
			"mtMaritalStsCd": "03",
			"dtRegistered": "2018-10-29 00:00:00",
			"mtCityCd": "110100",
			"mtCtryCd": "CN",
			"mtCityCdDscp": "市辖区(北京)",
			"mtStateCd": "110000",
			"mtResidenceStsCd": "01",
			"mobileNo": "15811266999",
			"mtIndvMobileUsageStsCd": "01",
			"mtEduLvlCd": "01",
			"email": "sadsad@qq.com",
			"weChat": "15811266999",
			"qq": "707768412"
		},
		"finance": {
			"hasCar": "Y",
			"hasCreditCard": "Y",
			"isFamily": "Y",
			"yearIncAmt": "12",
			"plateNo": "CF3964821",
			"creditCardLines": "231123213"
		},
		"emplymt": {
			"isBizEntity": "Y",
			"isComb": "Y",
			"bizRegNo": "999555666888777111",
			"bizAddr": "比较吵杨",
			"bizRegDtExpiry": "2023-06-28 00:00:00",
			"isLegalRep": "Y",
			"currentTotal": "12000",
			"yearSaleMarginsRate": "22",
			"ratal": "32000",
			"waterDosage": "22222",
			"electricityDosage": "22222",
			"workPhone": "22",
			"equityLine": "22222",
			"employees": "22",
			"salaryTotal": "22",
			"mtIndDetailCd": "c3062",
			"mtIndDetailCdDscp": "玻璃纤维增强塑料制品制造",
			"socialSecurity": "22222",
			"bizArea": "22222",
			"isBussLongEffec": "N",
			"employerNm": "北京",
			"employerPhone": "010-60394259",
			"mtJobSectorCd": "30200",
			"mtJobSectorCdDscp": "安全和消防人员",
			"prevServiceYr": null,
			"prevServiceMth": null,
			"mtPosHeldCd": null,
			"mtPosHeldCdDscp": null,
			"dtWorkInCurrIndustry": "2013-06-24 00:00:00",
			"isRelatedPerson": null,
			"mtIndCatCd": "c30",
			"mtIndCd": "c306",
			"mtIndTypCd": "c"
		}
	},
	"contact": [{
			"nm": "测试的联系人",
			"mobileNo": "15811269699",
			"mtPosHeldCd": "005",
			"email": "89asdsa@qq.com"
		},
		{
			"nm": "测试的联系人2",
			"mobileNo": "15811269888",
			"mtPosHeldCd": "005",
			"email": "biany@lianjintai.com"
		}
	],
	"fac": {
		"lt": "CP",
		"mtOrgCd": "1000",
		"no": "578",
		"mtFacCd": "103192",
		"mtFacPurCd": null,
		"lmtAppr": "12",
		"isRevolvingAllowed": "Y",
		"dtMaturity": null,
		"mtTimeCd": "M",
		"tenureAppr": "12",
		"mtTenantId": "1000",
		"mtFacCdDscp": "新建一个产品以测试",
		"mtFacTypCd": "1",
		"mtFacTypCdDscp": "贷款",
		"mtTimeCdDscp": null,
		"intRate": "12",
		"intRateInSuspense": "12",
		"mtRepymtTypCd": "005",
		"mtRepymtTypCdDscp": "005",
		"mtFacPurCds": null,
		"mtFacPurCdList": [{
			"mtFacPurCd": "1001"
		}],
		"mtFacPurCdDscp": null,
		"updateBy": null,
		"dtUpdated": null,
		"loanRemark": "{\"mtFacCd\":\"103192\",\"mtFacCdToFinDscp\":\"新建一个产品以测试\"}",
		"type": null,
		"deductAcctNo": "6039425988",
		"mtFacCatCd": "103",
		"mtFacCatCdDscp": "保理",
		"finalLmtAppr": null,
		"totalRepymtAmt": null,
		"totalDisbAmt": null,
		"mtFacCdToFinDscp": null,
		"mtIntRateTypCd": "Y",
		"mtIntRateTypCdDscp": "年利率",
		"isDelFac": "N",
		"loanType": "CP"
	},
	"doc": {
		"cifDocRefId": "bee503b47798415bb19382ab68aba1f1",
		"facDocRefId": "d317f08e5eb442738ebc9f82efd3c121"
	},
	"ccms": {
		"mtCpCreditModelCd": "N1",
		"options": [{
			"selected": ["A"],
			"cd": "chhfw"
		}, {
			"selected": ["A"],
			"cd": "cwgl"
		}, {
			"selected": ["A"],
			"cd": "gdzcld"
		}, {
			"selected": ["A"],
			"cd": "gjzc"
		}, {
			"selected": ["A"],
			"cd": "dfzc"
		}, {
			"selected": ["A"],
			"cd": "hytzhj"
		}, {
			"selected": ["A"],
			"cd": "qybj"
		}, {
			"selected": ["A"],
			"cd": "ssxfsc"
		}, {
			"selected": ["A"],
			"cd": "yjnl"
		}, {
			"selected": ["A"],
			"cd": "ywgc"
		}, {
			"selected": ["A"],
			"cd": "yysr"
		}, {
			"selected": ["A"],
			"cd": "zczj"
		}]
	}

}

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