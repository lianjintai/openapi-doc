# 借款人配偶信息
## 描述
创建借款方为个人，关联关系为配偶的关联人信息
## 规则
当借款人的婚姻状态为已婚有子女或已婚无子女时，必须添加一个关联关系为配偶的关联人，且只能添加一个，当借款人的婚姻状态不是已婚有子女或已婚无子女时，配偶关联人不能添加
## API代码
loan\_app:cif\_cs\_rel_spouse:create

## 请求参数

### 借款方为个人，关联关系为配偶
关联人信息由三部分组成：

| 名称 | 类型 | 是否必须 | 描述 | 备注 |
| --- | --- | --- | --- | --- |
| relCsBase | JSON | 是 | [关联人基本信息](#关联人基本信息) | |
| relCsEmploy | JSON | 否 | [关联人职业信息](#关联人职业信息) | 关联人基本信息中“是否为个体工商户/私营业主”为否时需要填写 | 
| relCsBusiness | JSON | 否 | [关联人经营信息](#关联人经营信息) | 关联人基本信息中“是否为个体工商户/私营业主”为是时需要填写 | 


#### 关联人基本信息
| 名称 | 类型 | 是否必须 |  最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| appId | String | 是 | 50 |申请ID（融资申请创建API返回的结果） | 0092728480d24f |
| mtCifRelCd | String | 是 | 20 |与借款方的关联关系 | II001 |
| nm | String | 是 | 80 | 关联人姓名（与身份证上相同） | 张三 |
| idNo | String | 是 | 50 | 身份证号码 |  |
| dtIssued | Date | 是 |  | 身份证签发日期 |  |
| dtExpiry | Date | 是 |  | 身份证到期日（长期身份证可以为空） |  |
| mtGenderCd | String | 是 | 20 | 性别 |  |
| mtMaritalStsCd | String | 是 | 20 | 婚姻情况 |  |
| dtRegistered | Date | 是 |  | 出生日期 |  |
| mtEduLvlCd | String | 否 | 20 | 最高学历 |  |
| mtCityCd | String | 否 | 20 | 所在城市 |  |
| mtResidenceStsCd | String | 否 | 20 | 本地居住情况 |  |
| isFamily | String | 否 | 1 | 是否自有房产 |  |
| nationalityMtCtryCd | String | 否 | 20 | 国籍 |  |
| mobileNo | String | 是 | 11 | 手机号 |  |
| mtIndvMobileUsageStsCd | String | 否 | 20 |  手机使用年限 |  |
| email | String | 否 | 50 |电子邮箱 |  |
| qq | Number | 否 |  15 | QQ号 |  |
| weChat | String | 否 |  50 | 微信号 |  |
| isBizEntity | String | 是 | 1 | 是否个体工商户／私营业主 | Y-是私营业主；N-非私营业主 |
| bankCard | Number | 是 |  14 (12,2)| 	银行卡流水总额（单位/元） |  |
| creditCardLines | Number | 否 |  14 (12,2)| 信用卡额度 |  |
| loanFixedYear | Number | 否 |  2 | 贷款记录年限 |  |
| yearIncAmt | String | 否 | 14 (12,2) | 近1年税后收入(单位/元)(单位/元) |  |


#### 关联人职业信息
关联人基本信息中选择非私营业主/个体工商户时需要输入：

| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| employerNm | String | 否 |  80 | 工作单位 |  |
| mtPosHeldCd | String | 否 |  20 | 职位|  |
| prevServiceYr | Number | 否 |  2 | 工作年限(年)|  |
| prevServiceMth | Number | 否 | 2 | 工作年限(月)|  |
| dtWorkInCurrIndustry | Date | 否 |   | 从事现行业时间 |  ||

#### 关联人经营信息
关联人基本信息中选择是私营业主/个体工商户时需要输入：

| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| isLegalRep | String | 否 |  1 | 是否法定代表人  |  |
| mtIndDetailCd | String | 否 |  50 | 行业类型 |  |
| bizRegNo | String | 否 |  50 | 营业执照号 |  |
| bizAddr | String | 否 |  50 | 经营地址 |  |
| bizArea | String | 否 |  200 | 经营范围 |  |
| currentTotal | Number | 否 |  20 (12,2) | 近一年流水总额（单位：元） | 大于0，小于999999999999.99的数字,小数点后保留2位小数 |
| waterDosage | Number | 否 |  14 (12,2)| 近一年用水量（单位：吨） |大于0，小于999999999999.99的数字,小数点后保留2位小数  |
| electricityDosage | Number | 否 |  14 (12,2)| 近一年用电量（单位：度） |大于0，小于999999999999.99的数字,小数点后保留2位小数  |
| ratal | Number | 否 |  14 (12,2)| 近一年纳税额（单位：元） |大于0，小于999999999999.99的数字,小数点后保留2位小数  |
| socialSecurity | Number | 否 |  14 (12,2)| 近一年社保缴存额 （单位：元） | 大于0，小于999999999999.99的数字,小数点后保留2位小数 |
| equityLine | Number | 否 |  14 (12,2)| 近一年公积金缴存额 （单位：元） |大于0，小于999999999999.99的数字,小数点后保留2位小数  |
| employees | Number | 否 |  12 | 员工人数 |  |
| salaryTotal | Number | 否 |  14 (12,2)| 近一年发放工资 （单位：元） |  大于0，小于999999999999.99的数字,小数点后保留2位小数|



## 响应参数
| 名称 | 类型 | 描述 |示例值 |
| --- | --- | --- | --- |
| appId | String | 申请ID | 0092728480d24f5d87bf63639b5cfe1c |

## 错误码
| 描述 | HTTP状态码 | 语义 |
| --- | --- | --- | 
| appId未找到 | 400 | 请输入正确的appId |

## 示例
### 请求示例（借款方为个人，关联关系为配偶）
#### 关联人非私营业主
```javascript
{
    "relCsBase": {
        "appId": "f1480dd2444f4850b8", 
        "bankCard": 1234556565, 
        "creditCardLines": 12345, 
        "dtExpiry": "2017-05-23 18:18:06", 
        "dtIssue": "2017-05-23 18:18:06", 
        "dtRegistered": "2017-05-23 18:18:06", 
        "email": "123@qq.com", 
        "idNo": "51c5d08d7c924d3a9f", 
        "isBizEntity": "N", 
        "isFamily": "Y", 
        "loanFixedYear": 11, 
        "mobileNo": "18888888888", 
        "yearIncAmt": 100000, 
        "mtCifRelCd": "II001", 
        "mtCityCd": "110100", 
        "mtEduLvlCd": "01", 
        "mtGenderCd": "M", 
        "mtIndvMobileUsageStsCd": "01", 
        "mtMaritalStsCd": "02", 
        "mtResidenceStsCd": "01", 
        "nm": "非私营关联人", 
        "qq": 12345, 
        "weChat": "1234"
    }, 
    "relCsEmploy": {
        "dtWorkInCurrIndustry": "2017-05-23 18:18:06", 
        "employerNm": "单位姓名", 
        "mtPosHeldCd": "001", 
        "prevServiceMth": 1, 
        "prevServiceYr": 2
    }
}
```

### 请求示例（借款方为个人，关联关系为配偶）
#### 关联人是私营业主
```javascript
{
    "relCsBase": {
        "appId": "a1537aee01c7421bb8", 
        "bankCard": 1234556565, 
        "creditCardLines": 12345, 
        "dtExpiry": "2017-05-23 18:26:45", 
        "dtIssue": "2017-05-23 18:26:45", 
        "dtRegistered": "2017-05-23 18:26:45", 
        "email": "123@qq.com", 
        "idNo": "814be0d9fa464c42b3", 
        "isBizEntity": "Y", 
        "isFamily": "Y", 
        "loanFixedYear": 11, 
        "mobileNo": "18888888888", 
        "yearIncAmt": 100000, 
        "mtCifRelCd": "II001", 
        "mtCityCd": "110100", 
        "mtEduLvlCd": "01", 
        "mtGenderCd": "M", 
        "mtIndvMobileUsageStsCd": "01", 
        "mtMaritalStsCd": "02", 
        "mtResidenceStsCd": "01", 
        "nm": "私营业主关联人", 
        "qq": 12345, 
        "weChat": "1234"
    }, 
    "relCsBusiness": {
        "bizAddr": "北京", 
        "bizArea": "电子商务", 
        "bizRegNo": "ef512680ed01492", 
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
}
```
### 返回示例
```javascript
{
    "appId": "0092728480d24f5d87bf63639b5cfe1c"
}
```
## FAQ
关于此文档暂时还没有FAQ
