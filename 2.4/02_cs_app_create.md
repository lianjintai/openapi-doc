# 个人授信申请创建
## 描述
仅支持个人贷款，包括借款人的信息、借款人配偶信息、借款人亲朋信息,贷款产品信息，接口传入的参数（参数名、字段类型、是否必填、字段长度、字段验证规则）通过“获取个贷产品配置”接口得到。
授信成功之后，需要保存响应参数中的“申请ID”，作为后续交易的请求参数。

当借款人已存在一笔新建或审批中的申请时，再次创建新申请会不允许创建（以证件号和证件类型作为条件）。
## API代码
loan_app:cs_app:create

## 请求参数
借款人为个人时，需要提供：
    1.个人借款人信息
        - 基本信息
        - 财务信息
        - 经营信息（个体工商户/私营业主）
        - 特色信息 贷款产品自定义信息
    2.关系图谱-配偶
        - 基本信息
        - 财务信息
        - 经营信息（个体工商户/私营业主）
    3.关系图谱-亲朋
            - 基本信息
            - 经营信息（非个体工商户/私营业主）
    4.贷款产品
    5.申请材料

参数结构定义如下：

| 名称 | 类型 | 是否必须 | 描述 | 
| --- | --- | --- | --- | 
| cif | JSON | 是 | 个人借款人信息，见[个人借款人信息](#个人借款人信息) |
| spouse | JSON | 否 | 关联图谱-配偶，见[关系图谱-配偶](#关系图谱-配偶)，关系图谱至少一个，如果借款人已婚，配偶信息必传 |
| family | JSON(List) | 否 | 关联图谱-亲朋，见[关系图谱-亲朋](#关系图谱-亲朋) |
| fac | JSON | 是 | 业务信息 见[业务信息](#业务信息) |
| doc | JSON | 否 | 申请材料 见[申请材料](#申请材料) |
| callbackURL | String | 否 | 授信状态变更后通知回调URL( 如:http://api.xxxx.com/ljt/callback )，见[授信状态变更通知回调](#授信状态变更通知回调) |

### 个人借款人信息
个人借款人信息由三部分组成：

| 名称 | 类型 | 是否必须 | 描述 | 备注 |
| --- | --- | --- | --- | --- |
| identity | JSON | 是 | 身份信息 | |
| finance | JSON | 否 | 财务信息 | |
| employ | JSON | 否 | 职业信息-非私营业主 或 职业信息-私营业主 | | 
| feature | JSON（List） | 否 | 特色信息 | | 


###  关系图谱-配偶
关联人关系为配偶需要输入的参数

| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| identity | JSON | 是 | 关系图谱-身份信息 | |
| finance | JSON | 否 |关系图谱-财务信息 | |
| employ | JSON | 否 | 关系图谱-职业信息-非私营业主 或 关系图谱-配偶-职业信息-私营业主 | | 

###  关系图谱-亲朋
关联人关系为配偶需要输入的参数

| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| identity | JSON | 是 | 关系图谱-身份信息 | |
| finance | JSON | 否 |关系图谱-财务信息 | |

### 申请材料
| 名称 | 类型 | 是否必须  | 描述 | 示例值 |
| --- | --- | --- | ---  | --- |
| cifDocRefId | string |  | 上传的申请材料的关联CIF的Id,此Id从获取产品配置接口中返回的refId |  |
| facDocRefId | string |  | 上传的申请材料的关联FAC的Id,此Id从获取产品配置接口中返回的refId  |  |


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

### 请求示例（个人）
#### 个人非私营业主-完整参数
```javascript
{
  "cif": {
    "feature": [
      {
        "name": "60d9da136de045118eacf903b4e01531",
        "value": "dddd",
        "label": "test"
      }
    ],
    "identity": {
      "nm": "姓名",
      "mtGenderCd": "F",
      "mtCifIdTypCd": "I",
      "mtCifIdTypCdDscp": "身份证",
      "idNo": "110113199506217906",
      "dtIssue": "2013-07-10 00:00:00",
      "dtExpiry": "2023-07-05 00:00:00",
      "mtMaritalStsCd": "01",
      "dtRegistered": "1995-06-21 00:00:00",
      "mtEduLvlCd": "01",
      "email": "912933515@qq.com",
      "mtResidenceStsCd": "01",
      "nationalityMtCtryCd": "CN",
      "mtStateCd": "110000",
      "mtStateCdDscp": null,
      "mtCityCd": "110100",
      "mtCityCdDscp": "市辖区(北京)",
      "mobileNo": "13839944397",
      "mtIndvMobileUsageStsCd": "01",
      "qq": "912933515",
      "weChat": "13839944397",
      "isLongEffec": "N",
      "mtCtryCd": "CN"
    },
    "finance": {
      "yearIncAmt": "1",
      "hasCreditCard": "Y",
      "creditCardLines": "1",
      "isFamily": "Y",
      "hasCar": "Y",
      "plateNo": "1"
    },
    "emplymt": {
      "employerNm": "工作单位",
      "mtJobSectorCd": "30200",
      "mtJobSectorCdDscp": "安全和消防人员",
      "prevServiceYr": "1",
      "prevServiceMth": "1",
      "mtPosHeldCd": "004",
      "employerPhone": "1111",
      "dtWorkInCurrIndustry": "2013-06-16 16:00:00",
      "isBizEntity": "N"
    }
  },
  "fac": {
    "dtMaturity": "2017-05-03 15:12:27",
    "intRate": 12,
    "intRateInSuspense": "11",
    "mtIntRateTypCd": "Y",
    "deductAcctNo": "16547718523633346",
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
  },
  "spouse": {
    "identity": {
      "mtCifRelCd": "II001",
      "isLongEffec": "N",
      "dtExpiry": "",
      "nm": "1111",
      "mtGenderCd": "M",
      "mtCifIdTypCd": "I2",
      "idNo": "11011319861222040X",
      "mtMaritalStsCd": "01",
      "dtRegistered": "2018-10-24 00:00:00",
      "mtCityCd": "500100",
      "mtCtryCd": "CN",
      "mtCityCdDscp": "市辖区(重庆)",
      "mtStateCd": "500000",
      "mtResidenceStsCd": "04",
      "mobileNo": "13880785548",
      "mtIndvMobileUsageStsCd": "04",
      "mtEduLvlCd": "04",
      "nationalityMtCtryCd": "CN",
      "email": "912933515@qq.com",
      "weChat": "13880785548",
      "qq": "912933515"
    },
    "finance": {
      "hasCar": "Y",
      "hasCreditCard": "Y",
      "isFamily": "Y",
      "yearIncAmt": "11",
      "plateNo": "11",
      "creditCardLines": "1"
    },
    "emplymt": {
      "employerNm": "工作单位",
      "mtJobSectorCd": "50300",
      "mtJobSectorCdDscp": "畜牧业生产人员",
      "prevServiceYr": "1",
      "prevServiceMth": "1",
      "mtPosHeldCd": "006",
      "employerPhone": "123",
      "dtWorkInCurrIndustry": "2013-06-24 00:00:00",
      "isBizEntity": "N"
    }
  },
  "family": [
    {
      "identity": {
        "nm": "ttt",
        "mtCifIdTypCd": "I2",
        "mtGenderCd": "M",
        "idNo": "234243",
        "dtRegistered": "1988-06-28 00:00:00",
        "mobileNo": "13819126032",
        "mtCifRelCd": "II002"
      },
      "finance": {
        "mtIncSourceCd": "ISC005",
        "yearIncAmt": "111111"
      }
    },
    {
      "identity": {
        "nm": "ttt",
        "mtCifIdTypCd": "I2",
        "mtGenderCd": "F",
        "idNo": "3431222",
        "dtRegistered": "1988-06-28 00:00:00",
        "mobileNo": "13891897842",
        "mtCifRelCd": "II002"
      },
      "finance": {
        "mtIncSourceCd": "ISC005",
        "yearIncAmt": "111111"
      }
    }
  ],
  "doc": {
    "cifDocRefId": "bee503b47798415bb19382ab68aba1f1",
    "facDocRefId": "d317f08e5eb442738ebc9f82efd3c121"
  }
}
```

#### 个人私营业主-完整
```javascript
{
  "cif": {
    "feature": [
      {
        "name": "60d9da136de045118eacf903b4e01531",
        "value": "dddd",
        "label": "test"
      }
    ],
    "identity": {
      "nm": "新姓名",
      "mtGenderCd": "F",
      "mtCifIdTypCd": "I",
      "idNo": "110113197611254128",
      "dtIssue": "2013-07-10 00:00:00",
      "dtExpiry": "2023-07-05 00:00:00",
      "mtMaritalStsCd": "01",
      "dtRegistered": "1976-11-25 00:00:00",
      "mtEduLvlCd": "01",
      "email": "912933515@qq.com",
      "mtResidenceStsCd": "01",
      "nationalityMtCtryCd": "CN",
      "mtStateCd": "110000",
      "mtCityCd": "110100",
      "mobileNo": "13839944397",
      "mtIndvMobileUsageStsCd": "01",
      "qq": "912933515",
      "weChat": "13839944397",
      "isLongEffec": "N",
      "mtCtryCd": "CN"
    },
    "finance": {
      "yearIncAmt": "1",
      "hasCreditCard": "Y",
      "creditCardLines": "1",
      "isFamily": "Y",
      "hasCar": "Y",
      "plateNo": "1"
    },
    "emplymt": {
      "isBizEntity": "Y",
      "isComb": "Y",
      "bizRegNo": "837806634833883944",
      "bizAddr": "123",
      "bizRegDtExpiry": "2023-06-19 16:00:00",
      "isLegalRep": "Y",
      "currentTotal": "1121",
      "yearSaleMarginsRate": "12",
      "ratal": "13",
      "waterDosage": "15",
      "electricityDosage": "14",
      "workPhone": "111",
      "equityLine": "17",
      "employees": "18",
      "salaryTotal": "19",
      "mtIndDetailCd": "b1093",
      "socialSecurity": "16",
      "bizArea": "111",
      "isBussLongEffec": "N",
      "mtJobSectorCd": "30200",
      "dtWorkInCurrIndustry": "2013-06-16 00:00:00",
      "mtIndCatCd": "b10",
      "mtIndCd": "b109",
      "mtIndTypCd": "b"
    }
  },
  "fac": {
    "dtMaturity": "2017-05-03 15:12:27",
    "intRate": 12,
    "isRevolvingAllowed": "Y",
    "mtIntRateTypCd": "Y",
    "intRateInSuspense": "11",
    "deductAcctNo": "16547718523633346",
    "lmtAppr": 123,
    "mtFacCd": "P1024",
    "mtFacPurCds": [
      "P101"
    ],
    "mtRepymtTypCd": "005",
    "mtTimeCd": "D",
    "tenureAppr": "12"
  },
  "spouse": {
    "identity": {
      "mtCifRelCd": "II001",
      "isLongEffec": "N",
      "dtExpiry": "",
      "nm": "1111",
      "mtGenderCd": "M",
      "mtCifIdTypCd": "I2",
      "idNo": "111111111111111",
      "mtMaritalStsCd": "01",
      "dtRegistered": "2018-10-24 00:00:00",
      "mtCityCd": "500100",
      "mtCtryCd": "CN",
      "mtStateCd": "500000",
      "mtResidenceStsCd": "04",
      "mobileNo": "13880785548",
      "mtIndvMobileUsageStsCd": "04",
      "mtEduLvlCd": "04",
      "nationalityMtCtryCd": "CN",
      "email": "912933515@qq.com",
      "weChat": "13880785548",
      "qq": "912933515"
    },
    "finance": {
      "hasCar": "Y",
      "hasCreditCard": "Y",
      "isFamily": "Y",
      "yearIncAmt": "11",
      "plateNo": "11",
      "creditCardLines": "1"
    },
    "emplymt": {
      "isComb": "Y",
      "bizRegNo": "493567133659322097",
      "bizAddr": "11",
      "bizRegDtExpiry": "2023-06-20 00:00:00",
      "isLegalRep": "Y",
      "currentTotal": "12",
      "yearSaleMarginsRate": "13",
      "ratal": "14",
      "electricityDosage": "15",
      "waterDosage": "16",
      "socialSecurity": "17",
      "equityLine": "18",
      "employees": "19",
      "salaryTotal": "20",
      "workPhone": "21",
      "mtIndDetailCd": "c3062",
      "mtIndCatCd": "c30",
      "mtIndCd": "c306",
      "mtIndTypCd": "c",
      "mtIndDetailCdDscp": "玻璃纤维增强塑料制品制造",
      "bizArea": "23",
      "isBizEntity": "Y",
      "isBussLongEffec": "N"
    }
  },
  "family": [
    {
      "identity": {
        "nm": "ttt",
        "mtCifIdTypCd": "I2",
        "mtGenderCd": "M",
        "idNo": "3431222",
        "dtRegistered": "1988-06-28 00:00:00",
        "mobileNo": "13891897842",
        "mtCifRelCd": "II002"
      },
      "finance": {
        "mtIncSourceCd": "ISC005",
        "yearIncAmt": "111111"
      }
    }
  ],
  "doc": {
    "cifDocRefId": "bee503b47798415bb19382ab68aba1f1",
    "facDocRefId": "d317f08e5eb442738ebc9f82efd3c121"
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
    "code": 400, 
    "message": "{cif.identity.idNo:[证件号为空;],cif.identity.nm:[姓名为空;],fac.mtFacCd:[贷款产品为空;]}", 
    "url": "", 
    "isConfirm": false, 
    "data": null
}
```


## FAQ
关于此文档暂时还没有FAQ