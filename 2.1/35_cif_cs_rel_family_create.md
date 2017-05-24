# 借款人亲朋信息
## 描述
创建借款方为个人，关联关系为父母、子女、兄弟姐妹、朋友的关联人信息

## 规则
    与借款人关联关系为父母时：最多只能添加两个关联人信息
    与借款人关联关系为子女时：可以添加一个或多个
    与借款人关联关系为兄弟姐妹时：可以添加一个或多个
    与借款人关联关系为朋友时：可以添加一个或多个

## API代码
loan\_app:cif\_cp\_rel_family:create

## 请求参数

### 借款方为个人，关联关系为父母、子女、兄弟姐妹、朋友
关联人基本信息：

| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| appId | String | 是 | 50 |申请ID（融资申请创建API返回的结果） | 0092728480d24f |
| mtCifRelCd | String | 是 | 20 |与借款方的关联关系 | II002-父母；II003-子女；II004-兄弟姐妹；II006-朋友 |
| nm | String | 是 | 80 | 关联人姓名（与身份证上相同） | 张三 |
| idNo | String | 否 | 50 | 身份证号码 |  |
| mtGenderCd | String | 否 | 20 | 性别 |  |
| mtMaritalStsCd | String | 否 | 20 | 婚姻情况 |  |
| dtRegistered | Date | 否 |  | 出生日期 |  |
| mobileNo | String | 否 | 11 | 手机号 |  |


## 响应参数
| 名称 | 类型 | 描述 |示例值 |
| --- | --- | --- | --- |
| appId | String | 申请ID | 0092728480d24f5d87bf63639b5cfe1c |

## 错误码
| 描述 | HTTP状态码 | 语义 |
| --- | --- | --- | 
| appId未找到 | 400 | 请输入正确的appId |

## 示例
### 请求示例（借款方为个人，关联关系为父母、子女、兄弟姐妹、朋友）

```javascript
[
    {
        "appId": "aea3ea7feb9240a9bb", 
        "dtRegistered": "2017-05-23 18:39:27", 
        "idNo": "838ac3ba1438494ba8", 
        "mobileNo": "18888888888", 
        "mtCifRelCd": "II002", 
        "mtGenderCd": "G", 
        "mtMaritalStsCd": "02", 
        "nm": "关联人母亲"
    }, 
    {
        "appId": "aea3ea7feb9240a9bb", 
        "dtRegistered": "2017-05-23 18:39:27", 
        "idNo": "2287978457824f1bad", 
        "mobileNo": "18888888888", 
        "mtCifRelCd": "II002", 
        "mtGenderCd": "M", 
        "mtMaritalStsCd": "02", 
        "nm": "关联人父亲"
    }
]
```
### 返回示例
```javascript
{
    "appId": "0092728480d24f5d87bf63639b5cfe1c"
}
```
## FAQ
关于此文档暂时还没有FAQ
