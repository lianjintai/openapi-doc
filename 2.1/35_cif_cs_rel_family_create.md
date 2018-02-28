# 借款人亲朋信息
## 描述
创建借款方为个人，关联关系为父母、子女、兄弟姐妹、朋友、同事的关联人信息

## 规则
    与借款人关联关系为子女时：可以添加一个或多个
    与借款人关联关系为兄弟姐妹时：可以添加一个或多个
    与借款人关联关系为朋友时：可以添加一个或多个
    与借款人关联关系为同事时：可以添加一个或多个

## API代码
loan\_app:cif\_cs\_rel_family:create

## 请求参数

### 借款方为个人，关联关系为父母、子女、兄弟姐妹、朋友
关联人基本信息：

| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| appId | String | 是 | 50 |申请ID（融资申请创建API返回的结果） | 0092728480d24f |
| mtCifRelCd | String | 是 | 20 |与借款方的关联关系 | II002-父母；II003-子女；II004-兄弟姐妹；II006-朋友；II007：同事 |
| nm | String | 是 | 80 | 关联人姓名（与身份证上相同） | 张三 |
| mtGenderCd | String | 是 | 20 | 性别 | F：女；M：男 |
| idNo | String | 否 | 18 | 身份证号码 |  |
| mtMaritalStsCd | String | 否 | 20 | 婚姻情况 |  |
| dtRegistered | Date | 否 |  | 出生日期 |  |
| mobileNo | String | 否 | 11 | 手机号 |  |
| mtIncSourceCd | String | 否 | 6 | 收入来源 | ISC001：工资、年薪；ISC002：退休、养老金；ISC003：住房公积金单位缴存部分；ISC004：住房补贴；ISC005：生产、经营、承包、承租所得； ISC005：生产、经营、承包、承租所得；ISC006：劳务报酬；ISC007：股息红利及利息所得；ISC008：其他所得；|


## 响应参数
| 名称 | 类型 | 描述 |示例值 |
| --- | --- | --- | --- |
| appId | String | 申请ID | 0092728480d24f5d87bf63639b5cfe1c |

## 错误码
| 描述 | HTTP状态码 | 语义 |
| --- | --- | --- | 
| appId未找到 | 400 | 请输入正确的appId |

## 示例
### 请求示例（借款方为个人，关联关系为父母、子女、兄弟姐妹、朋友、同事）

```javascript
{
    "appId": "aea3ea7feb9240a9bb", 
    "dtRegistered": "2017-05-23 18:39:27", 
    "idNo": "2287978457824f1bad", 
    "mobileNo": "18888888888", 
    "mtCifRelCd": "II002", 
    "mtGenderCd": "M", 
    "mtMaritalStsCd": "02",
    "mtIncSourceCd": "ISC001",
    "nm": "关联人父亲"
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
