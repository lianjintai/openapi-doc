#个贷-产品可配置所有字段

具体定义如下：

| 名称 | 类型 | 是否必须 | 描述 | 
| --- | --- | --- | --- | 
| cif | JSON |  是 | 个人借款人信息，见[个人借款人信息](#个人借款人信息) |
| spouse | json | 是 | 关系图谱-配偶，[关系图谱](#关系图谱)|  
| family | json | 是 | 关系图谱-亲朋，[关系图谱](#关系图谱) | 
| fac | JSON | 是 | 业务信息 见[业务信息](#业务信息) | 
| doc | JSON | 是 | 申请材料 见[申请材料](#申请材料) ||

## 个人借款人信息
个人借款人信息由三部分组成：

| 名称 | 类型 | 是否必须 | 描述 | 备注 |
| --- | --- | --- | --- | --- |
| identity | JSON | 是 | [身份信息](#身份信息) | |
| finance | JSON | 是 | [财务信息](#财务信息) | |
| emplymt | JSON | 否 | [职业信息-非私营业主](#职业信息-非私营业主) or [职业信息-私营业主](#职业信息-私营业主) | || 

### 身份信息
| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| nm | String | 是 | 300 | 借款人姓名（与身份证上相同） | 张三 |
| idNo | String | 是 | 50 | 身份证号码 |  |
| mtCifIdTypCd | String | 是 | 20 | 证件类型,[证件类型](dict_mtOther.md#证件类型) |  |
| nationalityMtCtryCd | String | 是 | 20 | 国籍  [国籍](dict_nationalityMtCtryCd.md#国家/国籍) |  |
| mtCityCd | String | 是 | 20 | 现常住地（市）[市](dict_nationalityMtCtryCd.md#市) |  |
| mtCtryCd | String | 是 | 20 | 现常住地（国家） [国家](dict_nationalityMtCtryCd.md#国家/国籍)|  |
| mtStateCd | String | 是 | 20 | 现常住地（省） [省](dict_nationalityMtCtryCd.md#省)|  |
| dtIssue | Date | 产品 |  | 身份证签发日期 时间格式：yyyy-MM-dd HH:mm:ss|  |
| dtExpiry | Date | 否 |  | 身份证到期日（长期身份证可以为空） |  |
| dtRegistered | Date | 否 |  | 出生日期 |  |
| isLongEffec | String | 否 |  | 证件到期日 是否长期有效 Y 或 N  |  |
| mtGenderCd | String | 否 | 20 | [性别](dict_mtOther.md#性别) |  |
| mtMaritalStsCd | String | 否 | 20 | [婚姻情况](dict_mtOther.md#婚姻情况) |  |
| mtEduLvlCd | String | 否 | 20 |  [最高学历](dict_mtOther.md#最高学历) |  |
| mtResidenceStsCd | String | 否 | 20 |  [本地居住情况](dict_mtOther.md#本地居住情况)|  |
| mobileNo | String | 否 | 20 | 手机号 |  |
| mtIndvMobileUsageStsCd | String | 否 | 20 |   [手机使用年限](dict_mtOther.md#手机使用年限)|  |
| email | String | 否 | 100 |电子邮箱 |  |
| qq | Number | 否 |  15 | QQ号 |  |
| weChat | String | 否 |  50 | 微信号 |  ||

### 财务信息
| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| yearIncAmt | String | 否 | 30 (26,4)| 个人年收入 |  |
| isFamily | String | 否 | 1 | 是否自有房产 |  |
| hasCar | String | 否 | 1 | 是否有车 |  |
| plateNo | String | 否 | 1 | 车牌号码 |  |
| hasCreditCard | String | 否 | 1 | 是否有信用卡 |  |
| creditCardLines | Number | 否 |  14 (12,2)| 信用卡额度 |  || 



### 职业信息-非私营业主
“是否为个体工商户/私营业主”为 "否" 时必须输入：

| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| isBizEntity | String | 是 | 1 | 是否个体工商户/私营业主 |  Y 或 N |
| employerNm | String | 否 |  100 | 工作单位 |  |
| mtJobSectorCd | String | 否 | 20 | [职业](dict_mtOther.md#职业) |  |
| prevServiceYr | Number | 否 |  60 | 工作年限(年)|  |
| prevServiceMth | Number | 否 |  12 | 工作年限(月)|  |
| mtPosHeldCd | String | 否 |  20 | [职位](dict_mtOther.md#职位) |  |
| employerPhone | String | 否 |  20 | 单位电话|  |
| dtWorkInCurrIndustry | Date | 否 |   | 从事现行业时间 时间格式：yyyy-MM-dd |  ||

### 职业信息-私营业主
“是否为个体工商户/私营业主”为“是”时必须输入：

| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| isComb | String | 否 |  1 | 是否多证合一  |  Y 或 N |
| bizRegNo | String | 否 |  50 | 营业执照号 或者 统一社会信用代码 |  |
| bizAddr | String | 否 |  50 | 经营地址 |  |
| bizRegDtExpiry | Date | 否 |  10 | 营业执照到期日 | 时间格式：yyyy-MM-dd |
| isBussLongEffec | String | 否 |  1 | 营业执照到期日是否长期，如果值为“Y”则不需要传入营业执照到期日 |  Y 或 N | 
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
| mtIndTypCd | String | 否 |  20 | [行业类型门类](dict_mtIndTypCd.md#行业类型门类) |  |
| mtIndCatCd | String | 否 |  20 | [行业类型大类](dict_mtIndTypCd.md#行业类型大类) |  |
| mtIndCd | String | 否 |  20 | [行业类型中类](dict_mtIndTypCd.md#行业类型中类) |  |
| mtIndDetailCd | String | 否 |  20 | [行业类型小类](dict_mtIndTypCd.md#行业类型小类) |  |
| bizArea | String | 否 |  255 | 经营范围 |  ||


##  关系图谱
关联人关系为配偶需要输入的参数

| 名称 | 类型 | 是否必须 | 描述 |
| --- | --- | --- | --- |
| identity | JSON | 是 | [关系图谱-配偶-身份信息](#关系图谱-配偶-身份信息) 或者 [关系图谱-亲朋-身份信息](#关系图谱-亲朋-身份信息) | 
| finance | JSON | 是 | [关系图谱-配偶-财务信息](#关系图谱-配偶-财务信息) 或者 [关系图谱-亲朋-财务信息](#关系图谱-亲朋-财务信息) |
| emplymt | JSON | 否 | [关系图谱-配偶-职业信息-非私营业主](#关系图谱-配偶-职业信息-非私营业主) 或者  [关系图谱-配偶-职业信息-私营业主](#关系图谱-配偶-职业信息-私营业主) ||

### 关系图谱-配偶-身份信息
| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| mtCifRelCd | String | 是 | 20 | [关联人关系](dict_mtOther.md#关联人关系) | |
| nm | String | 是 | 300 | 借款人姓名（与身份证上相同） | 张三 |
| idNo | String | 否 | 50 | 身份证号码 |  |
| mtCifIdTypCd | String | 否 | 20 | [证件类型](dict_mtOther.md#证件类型) |  |
| nationalityMtCtryCd | String | 否 | 20 | [国籍](dict_nationalityMtCtryCd.md#国家/国籍) |  |
| mtCityCd | String | 否 | 20 | 现常住地（市） [市](dict_nationalityMtCtryCd.md#市)|  |
| mtCtryCd | String | 否 | 20 | 现常住地（国家） [国家](dict_nationalityMtCtryCd.md#国家/国籍)|  |
| mtStateCd | String | 否 | 20 | 现常住地（省） [省](dict_nationalityMtCtryCd.md#省)|  |
| dtIssue | Date | 否 |  | 身份证签发日期 时间格式：yyyy-MM-dd HH:mm:ss|  |
| dtExpiry | Date | 否 |  | 身份证到期日（长期身份证可以为空） |  |
| dtRegistered | Date | 否 |  | 出生日期 |  |
| isLongEffec | String | 否 |  | 证件到期日 是否长期有效   | Y 或 N |
| mtGenderCd | String | 否 | 20 | [性别](dict_mtOther.md#性别)|  |
| mtMaritalStsCd | String | 否 | 20 | [婚姻情况](dict_mtOther.md#婚姻情况) |  |
| mtEduLvlCd | String | 否 | 20 | [最高学历](dict_mtOther.md#最高学历) |  |
| mtResidenceStsCd | String | 否 | 20 | [本地居住情况](dict_mtOther.md#本地居住情况) |  |
| mobileNo | String | 否 | 20 | 手机号 |  |
| mtIndvMobileUsageStsCd | String | 否 | 20 |  [手机使用年限](dict_mtOther.md#手机使用年限) |  |
| email | String | 否 | 100 |电子邮箱 |  |
| qq | Number | 否 |  15 | QQ号 |  |
| weChat | String | 否 |  50 | 微信号 |  ||

### 关系图谱-配偶-财务信息
| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| yearIncAmt | String | 否 | 30 (26,4)| 近1年税后收入(单位/元) |  |
| isFamily | String | 否 | 1 | 是否自有房产 |  |
| hasCar | String | 否 | 1 | 是否有车 |  |
| plateNo | String | 否 | 1 | 车牌号码 |  |
| hasCreditCard | String | 否 | 1 | 是否有信用卡 |  |
| creditCardLines | Number | 否 |  14 (12,2)| 信用卡额度 |  || 


### 关系图谱-配偶-职业信息-非私营业主
“是否为个体工商户/私营业主”为 "否" 时必须输入：

| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| isBizEntity | String | 是 | 1 | 是否个体工商户/私营业主 |  Y 或 N |
| employerNm | String | 否 |  100 | 工作单位 |  |
| mtJobSectorCd | String | 否 | 20 | [职业](dict_mtOther.md#职业) |  |
| prevServiceYr | Number | 否 |  60 | 工作年限(年)|  |
| prevServiceMth | Number | 否 |  12 | 工作年限(月)|  |
| mtPosHeldCd | String | 否 |  20 | [职位](dict_mtOther.md#职位)|  |
| employerPhone | String | 否 |  20 | 单位电话|  |
| dtWorkInCurrIndustry | Date | 否 |   | 从事现行业时间 时间格式：yyyy-MM-dd |  ||

### 关系图谱-配偶-职业信息-私营业主
“是否为个体工商户/私营业主”为“是”时必须输入：

| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| isBizEntity | String | 是 | 1 | 是否个体工商户/私营业主 |  Y 或 N |
| isComb | String | 否 |  1 | 是否多证合一  |  Y 或 N |
| bizRegNo | String | 否 |  50 | 营业执照号 或者 统一社会信用代码 |  |
| bizAddr | String | 否 |  50 | 经营地址 |  |
| bizRegDtExpiry | Date | 否 |  10 | 营业执照到期日 | 时间格式：yyyy-MM-dd |
| isBussLongEffec | String | 否 |  1 | 营业执照到期日是否长期，如果值为“Y”则不需要传入营业执照到期日 |  Y 或 N |
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
| mtIndTypCd | String | 否 |  20 | [行业类型门类](dict_mtIndTypCd.md#行业类型门类) |  |
| mtIndCatCd | String | 否 |  20 | [行业类型大类](dict_mtIndTypCd.md#行业类型大类) |  |
| mtIndCd | String | 否 |  20 | [行业类型中类](dict_mtIndTypCd.md#行业类型中类) |  |
| mtIndDetailCd | String | 否 |  20 | [行业类型小类](dict_mtIndTypCd.md#行业类型小类) |  |
| bizArea | String | 否 |  255 | 经营范围 |  ||


### 关系图谱-亲朋-身份信息
| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| mtCifRelCd | String | 是 | 20 | [关联人关系](dict_mtOther.md#关联人关系) |  |
| nm | String | 是 | 300 | 借款人姓名 |  |
| mtCifIdTypCd | String | 否 | 20 | [证件类型](dict_mtOther.md#证件类型) |  |
| idNo | String | 否 | 20 | 证件号码 |  |
| mtGenderCd | String | 是 | 20 | [性别](dict_mtOther.md#性别) |  |
| dtRegistered | Date | 否 | 10 | 出生日期 时间格式：yyyy-MM-dd HH:mm:ss|  |
| mobileNo | String | 是 | 20 | 手机号 |  ||

### 关系图谱-亲朋-财务信息
| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| mtIncSourceCd | String | 否 | 300 | [收入来源](dict_mtOther.md#收入来源) |  |
| yearIncAmt | String | 否 | 20(18.2) | 个人年收入 |  ||

## 业务信息

| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| mtFacCd | String | 是 | 20 | 贷款产品Cd |  |
| lmtAppr | Number | 是 | 30 (26,4)| 申请额度 |  |
| mtTimeCd | String | 是 | 1|  [业务期限类型](dict_mtFac.md#业务期限类型) | D |
| tenureAppr | Number | 是 | 6 | 业务期限 |  |
| mtIntRateTypCd | String | 是 | 20 | [利率类型](dict_mtFac.md#利率类型) | Y |
| mtRepymtTypCd | String | 是 | 20 | [偿还方式](dict_mtFac.md#偿还方式) |  |
| intRate | Number | 是 | 9 (5,4)| 年化利率 |  |
| isRevolvingAllowed | String | 是 | 1 | 授信额度是否可循环，默认为否 | Y 或 N |
| mtFacPurCds | JSON | 是 | 100 | [资金用途](dict_mtFac.md#资金用途)，可输入多个 | |
| intRateInSuspense | Number | 否 | 9 (5,4)| 罚息利率 |  |
| deductAcctNo | String | 否 | 23| 还款卡号 |  ||


## 申请材料
| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| url | Json | 是 |  | oss上传密钥 [阿里云oss上传签名密钥](#阿里云oss上传签名密钥) |  |
| docs | Json(list) | 是 |  | 申请材料列表 [业务上传申请材料列表](#业务上传申请材料列表) |  ||


### 阿里云oss上传签名密钥
| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| accessid | String | 是 | 20 |  |  |
| policy | String | 是 | 20 |  |  |
| signature | String | 是 | 20 |  |  |
| dir | String | 是 | 20 |  |  |
| host | String | 是 | 20 |  |  |
| callback | String | 是 | 20 |  |  ||

### 业务上传申请材料列表 
| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| mtDocTypeCd | String | 是 | 20 | 申请材料门类Cd, CIF:客户申请材料，FAC：业务申请材料|  |
| mtDocCd | String | 是 | 20 |   申请材料Cd，在上传申请材料的时候需要使用 ||
| mtDocCdDscp | String | 是 | 20 | 申请材料描述 |  |
| mtDocCatCd | String | 是 | 20 | 申请材料大类Cd |  |
| refId | String | 是 | 20 | 申请材料关联ID，在上传申请材料组织文件的时候，不同的申请材料门类，使用的refId不同。在"授信申请"的时候需要将申请材料门类为“CIF”的refId放入"doc.cifDocRefId"值中,门类为"FAC"的refId放入"doc.facDocRefId"值中 | |
| required | String | 是 | 20 |  是否必须，<font color=#ff0000 size=7 face="黑体">必传的申请材料将影响授信的审批</font>,Y:是，N:不是 |  ||
