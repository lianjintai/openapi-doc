#申请状态查询
## 描述
用于平台方查询申请状态，可以根据返回结果判断是否申请是否满足资金提供方的要求，如果已满足要求(响应参数中can\_push=Y时)，则可以调用 [融资申请推送API](20_app_push.md) 尝试推送申请到资金提供方审核 。

## API代码
loan\_app:app:sts

## 请求参数
| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| app_id | String | 是 | 50 | 申请ID（[融资申请创建API](05_app_create.md)返回的结果） | 0092728480d24f5d87bf63639b5cfe1c |
| mt_app_type_cd | String | 是 | 50 | 申请类型: CP_PUSH_APP-企业融资申请；CS_PUSH_APP-个人融资申请 | CP_PUSH_APP |

## 响应参数
| 名称 | 类型 | 描述 |示例值 |
| --- | --- | --- | --- |
| app_id | String | 申请ID | 0092728480d24f5d87bf63639b5cfe1c |
| mt_app_sts_cd | String | 申请状态代码，详细规则见:[申请状态](#申请状态) | APPROVED |
| rating | String | 评分结果 | 756 |
| can_push | String | 能否推送金融机构:Y-是；N-否 | Y |
| remark | String | 备注：当申请被退回或被取消时，返回退回或取消原因 | 风控审核未通过 |

###申请状态
| 申请类型 | 代码 | 描述 |
| --- | --- | --- |
| 企业融资申请 | APPROVED | 已批准，资金提供方已批准该笔融资申请 |
| 企业融资申请 | CANCELLED | 已取消，任务已经被取消，后续不能做任何操作 |
| 企业融资申请 | CP_PUSH_APP_PUSHED | 已推送，任务已发送到资金提供方，待对方审核 |
| 企业融资申请 | CP_PUSH_APP_RETURNED | 被退回，任务不满足风控审核，已被退回 |
| 企业融资申请 | CREATED | 录入中，可以上传申请材料，推送融资申请到资金提供方 |
| 个人融资申请 | APPROVED | 已批准，规则同企业融资申请 |
| 个人融资申请 | CANCELLED | 已取消，规则同企业融资申请 |
| 个人融资申请 | CREATED | 录入中，规则同企业融资申请 |
| 个人融资申请 | CS_PUSH_APP_PUSHED | 已推送，规则同企业融资申请 |
| 个人融资申请 | CS_PUSH_APP_RETURNED | 被退回，规则同企业融资申请 |

## 错误码
| 描述 | HTTP状态码 | 语义 |
| --- | --- | --- | 
| app_id未找到 | 400 | 请输入正确的app_id,或检查申请类型与申请ID是否匹配 |

## 示例
### 请求示例
```javascript
{
    "app_id":"0092728480d24f5d87bf63639b5cfe1c",
    "mt_app_type_cd":"CP_PUSH_APP"
}
```
### 返回示例
```javascript
{
    "app_id":"0092728480d24f5d87bf63639b5cfe1c",
    "mt_app_sts_cd":"APPROVED",
    "can_push":"N",
    "remark":""
}
```
##FAQ
关于此文档暂时还没有FAQ