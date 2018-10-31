#获取个贷产品配置	
## 描述
仅支持个人贷款，包括个贷字段配置、需要上传申请材料列表、OSS令牌
## API代码
loan_app:cs_fac:config

## 请求参数
| 名称 | 类型 | 是否必须 | 描述 | 示例值 |
| --- | --- | --- | --- | --- |
| mtFacCd | String | 是 | 贷款产品业务CD | P104820 |

## 响应参数
| 名称 | 类型 | 描述 |示例值 |
| --- | --- | --- | --- |
| cif | json | 授信时，客户信息需要数据字段及格式 |  |
| spouse | json | 授信时，关系图谱-配偶需要数据字段及格式| |  
| family | json | 授信时，关系图谱-亲朋需要数据字段及格式| |  
| fac | json | 授信时，贷款产品需要数据字段及格式 | |  
| doc | json | 授信时，需要上传的申请材料和上传OSS时需要的密钥 | |  


## 错误码
| 描述 | HTTP状态码 | 语义 |
| --- | --- | --- | 
| 贷款产品不存在 | 400 | 租户没有对应的产品。 |

## 示例
### 请求示例
```javascript
{
    "mtFacCd":"P104820"
}
```
### 返回示例
```javascript
{
    "fac": {
        "moduleName": "业务信息", 
        "description": null, 
        "fields": [
            {
                "fieldName": "贷款产品Cd", 
                "fieldAttr": "mtFacCd", 
                "fieldType": "SYS", 
                "fieldInfo": {
                    "option": "required", 
                    "editor": "Y", 
                    "area": null, 
                    "type": "input", 
                    "placeholder": null, 
                    "maxLength": 20, 
                    "width": null, 
                    "defaultValue": null, 
                    "pattern": "text", 
                    "errMsg": null, 
                    "regExp": null
                }
            }
        ]
    }, 
    "doc": {
        "url": {
            "accessid": "LTAIgSk2NJNg18Kr", 
            "policy": "......", 
            "signature": "9BGzxR8e1OjFZpIJ6Pu/X8KzM7Y=", 
            "dir": "doc/", 
            "host": "https://ljt-site-oss.oss-cn-beijing.aliyuncs.com", 
            "callback": "...."
        }, 
        "docs": [
            {
                "mtDocTypeCd": "CIF", 
                "mtDocCd": "PCIF319", 
                "mtDocCdDscp": "有效身份证件", 
                "mtDocCatCd": "CS", 
                "refId": "63ddf972adea4869b924cf227033e8f3", 
                "required": "Y"
            }, 
            {
                "mtDocTypeCd": "CIF", 
                "mtDocCd": "PCIF324", 
                "mtDocCdDscp": "婚姻状况证明", 
                "mtDocCatCd": "CS", 
                "refId": "63ddf972adea4869b924cf227033e8f3", 
                "required": "N"
            }
        ]
    }, 
    "cif": {
        "moduleName": "客户信息", 
        "description": "", 
        "modules": {
            "identity": {
                "moduleName": "身份信息", 
                "description": null, 
                "fields": [
                    {
                        "fieldName": "借款人姓名", 
                        "fieldAttr": "nm", 
                        "fieldType": "SYS", 
                        "fieldInfo": {
                            "option": "required", 
                            "editor": "N", 
                            "area": null, 
                            "type": "input", 
                            "placeholder": null, 
                            "maxLength": 300, 
                            "width": null, 
                            "defaultValue": null, 
                            "pattern": "text", 
                            "errMsg": null, 
                            "regExp": null
                        }
                    }
                ]
            }, 
            "finance": {
                "moduleName": "财务信息", 
                "description": null, 
                "fields": [ ]
            }, 
            "emplymt": {
                "moduleName": "职业信息/经营信息", 
                "description": null, 
                "fields": [
                    {
                        "fieldName": "是否个体工商户/私营业主", 
                        "fieldAttr": "isBizEntity", 
                        "fieldType": "SYS", 
                        "fieldInfo": {
                            "option": "required", 
                            "editor": "N", 
                            "area": null, 
                            "type": "input", 
                            "placeholder": "示例:Y/N", 
                            "maxLength": 1, 
                            "width": null, 
                            "defaultValue": null, 
                            "pattern": "text", 
                            "errMsg": null, 
                            "regExp": null
                        }
                    }
                ]
            }, 
            "feature": {
                "moduleName": "特色信息", 
                "description": null, 
                "fields": [
                    {
                        "fieldName": "test", 
                        "fieldAttr": "60d9da136de045118eacf903b4e01531", 
                        "fieldType": "CUSTOM", 
                        "fieldInfo": {
                            "option": "optional", 
                            "editor": "Y", 
                            "area": null, 
                            "type": "input", 
                            "placeholder": "", 
                            "maxLength": 111, 
                            "width": 1, 
                            "defaultValue": "", 
                            "pattern": "text", 
                            "errMsg": "请填写正确的单行文本", 
                            "regExp": "/.*/"
                        }
                    }
                ]
            }
        }
    }, 
    "spouse": {
        "moduleName": "关系图谱-配偶，当借款人的婚姻状态为已婚有
 子女或已婚无子女时，必须添加一个关联关系为配偶的关联人，
 且只能添加一个，当借款人的婚姻状态不是已婚有子女或已婚无 子女时，配偶关联人不能添加", 
        "description": null, 
        "modules": {
            "identity": {
                "moduleName": "身份信息", 
                "description": null, 
                "fields": [
                    {
                        "fieldName": "关联人关系", 
                        "fieldAttr": "mtCifRelCd", 
                        "fieldType": "SYS", 
                        "fieldInfo": {
                            "option": "required", 
                            "editor": "Y", 
                            "area": null, 
                            "type": "input", 
                            "placeholder": null, 
                            "maxLength": 20, 
                            "width": null, 
                            "defaultValue": null, 
                            "pattern": "text", 
                            "errMsg": null, 
                            "regExp": null
                        }
                    }
                ]
            }, 
            "finance": {
                "moduleName": "财务信息", 
                "description": null, 
                "fields": [
                    {
                        "fieldName": "年收入", 
                        "fieldAttr": "yearIncAmt", 
                        "fieldType": "SYS", 
                        "fieldInfo": {
                            "option": "required", 
                            "editor": "Y", 
                            "area": null, 
                            "type": "money", 
                            "placeholder": "123.45", 
                            "maxLength": 50, 
                            "width": null, 
                            "defaultValue": null, 
                            "pattern": "money", 
                            "errMsg": null, 
                            "regExp": ""
                        }
                    }
                ]
            }, 
            "emplymt": {
                "moduleName": "职业信息", 
                "description": null, 
                "fields": [
                    {
                        "fieldName": "是否个体工商户/私营业主", 
                        "fieldAttr": "isBizEntity", 
                        "fieldType": "SYS", 
                        "fieldInfo": {
                            "option": "required", 
                            "editor": "N", 
                            "area": null, 
                            "type": "input", 
                            "placeholder": "示例:Y/N", 
                            "maxLength": 1, 
                            "width": null, 
                            "defaultValue": null, 
                            "pattern": "text", 
                            "errMsg": null, 
                            "regExp": null
                        }
                    }
                ]
            }
        }
    }, 
    "family": {
        "moduleName": "关系图谱-亲朋信息，
2关联关系为父母、 子女、兄弟姐妹、朋友、同事的关联人可以添加一个或多个", 
        "description": null, 
        "modules": {
            "identity": {
                "moduleName": "身份信息", 
                "description": null, 
                "fields": [
                    {
                        "fieldName": "关联人关系", 
                        "fieldAttr": "mtCifRelCd", 
                        "fieldType": "SYS", 
                        "fieldInfo": {
                            "option": "required", 
                            "editor": "Y", 
                            "area": null, 
                            "type": "input", 
                            "placeholder": null, 
                            "maxLength": 20, 
                            "width": null, 
                            "defaultValue": null, 
                            "pattern": "text", 
                            "errMsg": null, 
                            "regExp": null
                        }
                    }
                ]
            }, 
            "finance": {
                "moduleName": "财务信息", 
                "description": null, 
                "fields": [
                    {
                        "fieldName": "收入来源", 
                        "fieldAttr": "mtIncSourceCd", 
                        "fieldType": "SYS", 
                        "fieldInfo": {
                            "option": "optional", 
                            "editor": "N", 
                            "area": null, 
                            "type": "input", 
                            "placeholder": null, 
                            "maxLength": 20, 
                            "width": null, 
                            "defaultValue": null, 
                            "pattern": "text", 
                            "errMsg": null, 
                            "regExp": null
                        }
                    }
                ]
            }
        }
    }
}
```

[产品所有配置字段](cs_fac_all_config.html)

## FAQ
关于此文档暂时还没有FAQ