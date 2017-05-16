#申请材料上传
## 描述

## 限制
单次上传文件内容最大为100M，超过限制请分多次上传。

## API代码
loan\_app:doc:upload


## 请求参数
| 名称 | 类型 | 是否必须 | 描述 | 示例值 |
| --- | --- | --- | --- | --- |
| appId | String | 是 | 申请ID（[融资申请创建API](20_app_push.md)返回的结果） | 0092728480d24f5d87bf63639b5cfe1c |
| mt_app_type_cd | String | 是 | 申请类型: CP_PUSH_APP-企业融资申请；CS_PUSH_APP-个人融资申请 | CP_PUSH_APP |

## 响应参数
| 名称 | 类型 | 描述 |示例值 |
| --- | --- | --- | --- |
| app_id | String | 申请ID | 0092728480d24f5d87bf63639b5cfe1c |
| mtAppStsCd | String | 申请状态代码，详细规则见[附件](3_%E9%99%84%E4%BB%B6.html#申请状态) | APPROVED |
| can_push | String | 能否推送金融机构:Y-是；N-否 | Y |
| remark | String | 备注：当申请被退回或被取消时，返回退回或取消原因 | 风控审核未通过 |

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
## FAQ
关于此文档暂时还没有FAQ