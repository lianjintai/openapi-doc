#企贷-产品可配置所有字段

具体定义如下：

| 名称 | 类型 | 是否必须 | 描述 | 
| --- | --- | --- | --- | 
| cif | JSON | 是 | 企业信息 见[企业信息](#企业信息) |
| biz | JSON | 是 | 经营信息 见[经营信息](#企业经营信息) |
| rels | JSON | 是 | 企业主要成员 见[企业主要成员](#企业主要成员) |
| contact | JSON(List) | 是 | 联系人信息，见[联系人信息](#企业联系人信息) |
| fac | JSON | 是 | 业务信息， 见[业务信息](#企业业务信息) |
| doc | JSON | 是 | 申请材料信息， 见[申请材料](#申请材料) ||

## 企业信息
企业借款人信息由三部分组成

| 名称 | 类型 | 是否必须 | 描述 | 
| --- | --- | --- | --- | 
| corporate | JSON | 是 | 客户信息 见[客户信息](#客户信息) |
| taxInfo | JSON | 是 | 工商税务信息 见[工商税务信息](#工商税务信息) |
| bizCertificates | JSON | 是 | 经营许可证信息 见[经营许可证信息](#经营许可证信息) ||

## 客户信息
| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| nm | String | 是 | 300 | 企业名称(与营业执照上一致) | 北京某某公司 |
| isComb | String | 是 | 1 | 是否三证合一 |  |
| idNo | String | 是 | 50 | 统一社会信用代码(是否多证合一为是) |  |
| idNo | String | 是 | 50 | 营业执照号码(是否多证合一为否) |  |
| mtCtryCd | String | 是 | 20 | 所在城市(国家)  [国家](dict_nationalityMtCtryCd.md#国家/国籍)|  |
| mtStateCd | String | 是 | 20 | 所在城市(省份)   [省](dict_nationalityMtCtryCd.md#省) |  |
| mtCityCd | String | 是 | 20 | 所在城市(区域)  [市](dict_nationalityMtCtryCd.md#市)|  |
| mtCorpSalutationCd | String | 是 | 20 | [公司类型](dict_mtOther.md#公司类型) |  |
| principalNo | String | 是 | 20 | 联系电话 |  |
| mtListedCd | String | 否 | 20 | 是否上市 |  | 
| stockCode | String | 否 | 20 | 股票代码 |  |
| coreBiz | String | 是 | 255 | 主营业务 |  |
| brandNm | String | 是 | 200 |  核心产品及品牌 |  |
| mtCifCatCd | String | 是 | 200 | [资本金来源](dict_mtOther.md#资本金来源)|  |
| mtFinInsttnCd | String | 是 | 20 | [基本开户行](dict_mtOther.md#基本开户行) |  | 
| nationalityMtCtryCd | String | 是 | 20 | [注册国家](dict_nationalityMtCtryCd.md#国家/国籍) |  |
| grpNm | String | 是 | 100 | 集团名称 |  |
| isFreeTradeArea | String | 是 | 1 |  是否自贸区 |  |
| mtIndCatCd | String | 否 |  20 | [行业类型大类](dict_mtIndTypCd.md#行业类型大类) |  |
| mtIndCd | String | 否 |  20 | [行业类型中类](dict_mtIndTypCd.md#行业类型中类) |  |
| mtIndDetailCd | String | 否 |  20 | [行业类型小类](dict_mtIndTypCd.md#行业类型小类) |  |
| website | String | 是 | 50 | 网址 |  ||

## 工商税务信息
| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| dtRegistered | Date | 是 |  | 注册日期 |  | 
| authCapital | Number | 是 | 30 (26,4)| 注册资本(单位/万元) |  |
| registeredAddr | String | 是 | 20 | 注册地址 |  | 
| bizRegDtExpiry | String | 是 | 20 | 营业执照到期日 |  |
| bizRegNo | String | 是 | 20 | 中征码 |  ||

## 经营许可证信息

| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| no | String | 是 | 50 | 经营许可证编号 |  |
| mtBizCertificateTypCd | String | 是 | 2 | [经营许可证类型](dict_mtOther.md#经营许可证类型) |  |
| dtExpiry | Date | 是 |  | 经营许可证到期日 |  ||

## 企业经营信息
企业经营信息由以下信息组成

| 名称 | 类型 | 是否必须 | 描述 | 
| --- | --- | --- | --- | 
| businessInfo | JSON | 是 | 经营信息 见[经营信息](#经营信息) ||

### 经营信息
| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| dtCommenceTrading | date | 是 | 50 | 开始营业日期 |  | 
| bizAddr | String | 是 | 50 | 经营地址 |  | 
| saleAmt | Number | 是 | 30 (26,4)| 近一年销售额(单位/元) |  |
| ratal | Number | 是 | 14 (12,2)| 近一年纳税额(单位/元) |  |
| employeeCnt | String | 是 | 30| 员工数 |  |
| assetAmt | Number | 是 | 30 (26,4)| 资产价值(单位/元) |  |
| mtBizLandOwnerCd | String | 是 | 20 | [经营场地所有权](dict_mtOther.md#经营场地所有权) |  |
| bizLandArea | Number | 否 | 8  | 经营场地面积(单位/平方米) |  |
| waterDosage | Number | 是 | 14 (12,2)| 近一年用水量(单位/吨) |  |
| electricityDosage | Number | 是 | 14 (12,2)| 近一年用电量(单位/度) |  |
| salaryTotal | Number | 否 | 14 (12,2)| 近一年发放工资(单位/元) |  |
| mtSalaryTypCd | String | 否 | 1 | [工资发放方式](dict_mtOther.md#工资发放方式)|  |
| socialSecurity | Number (12,2)| 否 | 14 | 近一年社保缴存额(单位/元) |  | 
| equityLine | Number | 否 | 14 (12,2)| 近一年公积金缴存额(单位/元) |  | 
| noOfBizSite | Number | 是 | 3 | 营业网点数量(单位/个) |  ||


## 企业主要成员
企业主要成员信息由以下信息组成

| 名称 | 类型 | 是否必须 | 描述 | 
| --- | --- | --- | --- | 
| legalRelInfo | JSON | 是 | 关联信息 见[关联信息](#关联信息) |
| identity | JSON | 是 | 身份信息 见[身份信息](#身份信息) |
| finance | JSON | 是 | 财务信息 见[财务信息](#财务信息) |
| emplymt | JSON | 是 | [职业信息-非私营业主](#职业信息-非私营业主) or [职业信息-私营业主](#职业信息-私营业主) ||

### 关联信息
| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| mtCifRelCd | String | 是 | 20 | 关联人关系 |  |
| isActualCtrl | String | 是 | 1 | 是否实际控制人 |  |
| isInvolvedMgmt | String | 否 | 1 | 公司日常管理 |  |
| mtPosHeldCd | String | 否 | 20 | 管理职位 |  |
| dtInCompSince | String | 否 |  | 加入公司时间，yyyy-MM-dd |  |
| dtInBizLineSince | String | 否 |  | 进入本行业时间，yyyy-MM-dd |  |
| mgmtExperience | String | 否 | 200 | 工作经历|  |


### 身份信息
| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| nm | String | 是 | 300 | 借款人姓名（与身份证上相同） | 张三 |
| idNo | String | 是 | 50 | 身份证号码 |  |
| mtCifIdTypCd | String | 是 | 20 | [证件类型](dict_mtOther.md#证件类型) |  |
| nationalityMtCtryCd | String | 是 | 20 | 国籍  [国籍](dict_nationalityMtCtryCd.md#国家/国籍) |  |
| mtCityCd | String | 是 | 20 | 现常住地（市）[市](dict_nationalityMtCtryCd.md#市) |  |
| mtCtryCd | String | 是 | 20 | 现常住地（国家） [国家](dict_nationalityMtCtryCd.md#国家/国籍)|  |
| mtStateCd | String | 是 | 20 | 现常住地（省） [省](dict_nationalityMtCtryCd.md#省)|  |
| dtIssue | Date | 否 |  | 身份证签发日期 时间格式：yyyy-MM-dd HH:mm:ss|  |
| dtExpiry | Date | 否 |  | 身份证到期日（长期身份证可以为空） |  |
| dtRegistered | Date | 否 |  | 出生日期 |  |
| isLongEffec | String | 否 |  | 证件到期日 是否长期有效 Y 或 N  |  |
| mtGenderCd | String | 否 | 20 | [性别](dict_mtOther.md#性别) |  |
| mtMaritalStsCd | String | 否 | 20 | [婚姻情况](dict_mtOther.md#婚姻情况) |  |
| mtEduLvlCd | String | 否 | 20 | [最高学历](dict_mtOther.md#最高学历) |  |
| mtResidenceStsCd | String | 否 | 20 | [本地居住情况](dict_mtOther.md#本地居住情况) |  |
| mobileNo | String | 否 | 20 | 手机号 |  |
| mtIndvMobileUsageStsCd | String | 否 | 20 |  [手机使用年限](dict_mtOther.md#手机使用年限) |  |
| email | String | 否 | 100 |电子邮箱 |  |
| qq | Number | 否 |  15 | QQ号 |  |
| weChat | String | 否 |  50 | 微信号 |  ||

### 财务信息
| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| yearIncAmt | String | 否 | 30 (26,4)| 近1年税后收入(单位/元) |  |
| isFamily | String | 否 | 1 | 是否自有房产 |  |
| hasCar | String | 否 | 1 | 是否有车 |  |
| plateNo | String | 否 | 1 | 车牌号码 |  |
| hasCreditCard | String | 否 | 1 | 是否有信用卡 |  |
| creditCardLines | Number | 否 |  14 (12,2)| 信用卡额度 |  ||

“是否为个体工商户/私营业主”为 "否" 时必须输入：

### 职业信息-非私营业主
| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| isBizEntity | String | 是 | 1 | 是否个体工商户/私营业主 |  示例:Y/N |
| employerNm | String | 否 |  100 | 工作单位 |  |
| mtJobSectorCd | String | 否 | 20 | [职业](dict_mtOther.md#职业) |  |
| prevServiceYr | Number | 否 |  60 | 工作年限(年)|  |
| prevServiceMth | Number | 否 |  12 | 工作年限(月)|  |
| mtPosHeldCd | String | 否 |  20 | [职位](dict_mtOther.md#职位)|  |
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
| mtIndTypCd | String | 否 |  20 | [行业类型门类](dict_mtIndTypCd.md#行业类型门类) |  |
| mtIndCatCd | String | 否 |  20 | [行业类型大类](dict_mtIndTypCd.md#行业类型大类) |  |
| mtIndCd | String | 否 |  20 | [行业类型中类](dict_mtIndTypCd.md#行业类型中类) |  |
| mtIndDetailCd | String | 否 |  20 | [行业类型小类](dict_mtIndTypCd.md#行业类型小类) |  |
| bizArea | String | 否 |  255 | 经营范围 |  ||

## 企业联系人信息
| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| nm | String | 是 | 100 | 联系人姓名 | |
| mobileNo | String | 是 | 20 | 联系人手机号 | |
| mtCifContactCd | String | 是 | 20 | 与[客户关系](dict_mtOther.md#客户关系)，借款人为个人时必需 | |
| mtPosHeldCd | String | 是 | 20 |  [职位](dict_mtOther.md#职位)，借款人为企业时必需 | |
| email | String | 否 | 50 | 联系人邮箱 | ||


## 企业业务信息

| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| mtFacCd | String | 是 | 20 | 业务类型 |  |
| lmtAppr | Number | 是 | 30 (26,4)| 申请额度 |  |
| dtMaturity | Date | 否 |  | 到期日 |  |
| tenureAppr | Number | 是 | 6 | 业务期限 |  |
| mtTimeCd | String | 是 | 1| [业务期限类型](dict_mtFac.md#业务期限类型) |
| mtRepymtTypCd | String | 是 | 20 | [偿还方式](dict_mtFac.md#偿还方式) |  |
| isRevolvingAllowed | String | 是 | 1 | 授信额度是否可循环，默认为否 | Y/N |
| mtFacPurCds | JSON | 是 | 100 | [资金用途](dict_mtFac.md#资金用途)，可输入多个 |  |
| intRate | Number | 是 | 9 (5,4)| 年化利率 |  |
| intRateInSuspense | Number | 否 | 9 (5,4)| 罚息利率 |  ||

## 申请材料
| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| url | Json | 是 |  | oss上传密钥 [oss上传密钥](#oss上传密钥) |  |
| docs | Json(list) | 是 |  | 申请材料列表 [业务上传申请材料列表](#业务上传申请材料列表) |  ||


### oss上传密钥
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
| mtDocTypeCd | String | 是 | 20 | 申请材料门类Cd |  |
| mtDocCd | String | 是 | 20 |  | 申请材料Cd，在上传申请材料的时候需要使用 |
| mtDocCdDscp | String | 是 | 20 | 申请材料描述 |  |
| mtDocCatCd | String | 是 | 20 | 申请材料大类Cd |  |
| refId | String | 是 | 20 |  | 申请材料关联ID，在上传申请材料的时候需要使用 |
| required | String | 是 | 20 |  是否必须，Y是，N不是 |  ||