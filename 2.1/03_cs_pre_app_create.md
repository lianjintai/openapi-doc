# 借款预申请创建
## 描述
支持个人提交简单资料，进行贷款意向的收集。创建成功后，需要保存响应参数中的“申请ID”，作为后续交易的请求参数。

## API代码
loan\_app:cs_pre_app:create

## 请求参数

| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| custId | String | 是 | 50 | 借款人在平台方的客户ID或编号，能够唯一标识某一客户 | 0092728480d24f5d8 |
| nm | String | 是 | 300 | 借款人姓名（与身份证上相同） | 张三 |
| idNo | String | 是 | 50 | 身份证号码 |  |
| mtGenderCd | String | 是 | 20 | 性别 |  |
| mtMaritalStsCd | String | 是 | 20 | 婚姻情况 |  |
| mtEduLvlCd | String | 是 | 20 | 最高学历 |  |
| mtResidenceStsCd | String | 是 | 20 | 本地居住情况 |  |
| isFamily | String | 是 | 1 | 是否自有房产 |  |
| mtJobSectorCd | String | 是 | 20 | 职业 |  |
| mtCityCd | String | 是 | 20 | 所在城市 |  |
| mobileNo | String | 是 | 20 | 手机号 |  |
| creditCardLines | Number | 否 |  14 (12,2)| 信用卡额度 |  |
| portrait | JSON | 否 | 1000 | 客户画像 | {"芝麻评分":"698"}|
| lmtAppr | Number | 是 | 30 (26,4)| 申请额度 |  |
| tenureAppr | Number | 是 | 6 | 业务期限 |  |
| mtTimeCd | String | 是 | 1| 业务期限类型（D-天、M-月、Y-年） |  |
| intRate | Number | 是 | 9 (5,4)| 年化利率 |  |

## 响应参数
| 名称 | 类型 | 描述 |示例值 |
| --- | --- | --- | --- |
| app_id | String | 申请ID | 0092728480d24f5d87bf63639b5cfe1c |

## 错误码
| 描述 | HTTP状态码 | 语义 |
| --- | --- | --- | 
| nm不能为空 | 400 | 请检查nm字段是否传值 |
| 存在在途申请 | 405 | 客户的前一笔融资请求尚未批准或取消，无法发起新融资申请 |
## 示例
### 请求示例（个人）
```javascript
{
   
    "custId": "77f392388c2e410684", 
    "idNo": "1867fc918fdc4e349e", 
    "isFamily": "Y", 
    "mobileNo": "18888888888", 
    "creditCardLines":10000
    "mtCityCd": "110100", 
    "mtEduLvlCd": "01", 
    "mtGenderCd": "M", 
    "mtJobSectorCd": "10000", 
    "mtMaritalStsCd": "02", 
    "mtResidenceStsCd": "01", 
    "nm": "张三", 
    "intRate": 123, 
    "lmtAppr": 123, 
    "mtTimeCd": "M", 
    "tenureAppr": "12",
    "portrait": "{\"芝麻信用分\":\"750\"}"
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