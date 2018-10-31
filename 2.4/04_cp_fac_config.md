#获取企贷产品配置	
## 描述
仅支持企业贷款，包括企贷字段配置、需要上传申请材料列表、OSS令牌
## API代码
loan_app:cp_fac:config

## 请求参数
| 名称 | 类型 | 是否必须 | 描述 | 示例值 |
| --- | --- | --- | --- | --- |
| mtFacCd | String | 是 | 贷款产品业务CD | 1010 |

## 响应参数
| 名称 | 类型 | 描述 |示例值 |
| --- | --- | --- | --- |
| cif | json | 授信时，客户信息所需要的数据字段及格式 [模块](#模块)|  |
| biz | json | 授信时，经营信息所需要的数据字段及格式 [模块](#模块)|  |
| rels | json | 授信时，主要成员所需要的数据字段及格式 [模块](#模块)| |  
| contact | json | 授信时，主要成员中联系人所需要的数据字段及格式 [模块](#模块)| |
| fac | json | 授信时，贷款产品所需要的数据字段及格式 [模块](#模块)| |  
| doc | json | 授信时，所需要上传的申请材料和上传OSS时需要的密钥 | |  

## 模块
| 名称 | 类型 | 描述 |示例值 |
| --- | --- | --- | --- |
| moduleName | String | 模块名称 |  |
| description | String | 描述模块具体做什么，有什么规则等详细说明 |  |
| fields | JSON(List) | 模块包含的字段列表 [字段](#字段)|  |
| modules | JSON(List) | 模块包含的子模块列表 同字段列表只存在一个 [模块](#模块)|  |


## 字段
| 名称 | 类型 | 描述 |示例值 |
| --- | --- | --- | --- |
| fieldName | String | 字段中文名称 |  |
| fieldAttr | String | 字段name，授信时传入的参数名 |  |
| fieldType | String | 字段类型，SYS:系统，CUSTOM：自定义字段 |  |
| fieldInfo | JSON | [字段属性](#字段属性) |  |

## 字段属性
| 名称 | 类型 | 描述 |示例值 |
| --- | --- | --- | --- |
| option | String | 授信时是否需要传入，required：必传，optional：可选 |  |
| editor | String | 是否允许编辑，Y:是，N:否 |  |
| area | String | 表单中是否选择的区域参数，例如：是否经营业主，是：需要传入的字段area=1，否：要传入的字段area=2 |  |
| type | String | 字段类型，date：日期 input：文本  money:金额  number：非金额数字|  |
| placeholder | String | 字段详细说明，包括格式和示例值 |  |
| maxLength | String | 字段最大长度 |  |
| width | String | 表单渲染占用的宽度，例如，表单1行3列，一个字段占用2列，则值为2 |  |
| defaultValue | String | 默认值 |  |
| pattern | String | 字段格式，同type一起判断字段参数类型， money.money:金额正数、 money.thsdSept:金额保留两位小数（千位符）、 input.text:普通文本、date.datePicker:时间 、 number.unsigned:正整数、 number.money:正数,保留两位小数 |  |
| errMsg | String | 校验错误信息 |  |
| regExp | String | 校验正则表达式 |  |

## 错误码
| 描述 | HTTP状态码 | 语义 |
| --- | --- | --- | 
| acctNo未找到 | 400 | 请输入正确的appId,或检查申请类型与申请ID是否匹配 |

## 示例
### 请求示例
```javascript
{
    "mtFacCd":"1010"
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
                "fieldName": "贷款产品", 
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
            "policy": "...==", 
            "signature": "gOZM5dyMArxNI8kK6IULiAx6mW4=", 
            "dir": "doc/", 
            "host": "https://ljt-site-oss.oss-cn-beijing.aliyuncs.com", 
            "callback": "..."
        }, 
        "docs": [
            {
                "mtDocTypeCd": "CIF", 
                "mtDocCd": "PCIF101", 
                "mtDocCdDscp": "经年检合格的营业执照", 
                "mtDocCatCd": "CP", 
                "refId": "fd428a99b5734179939debc027f1b681", 
                "required": "N"
            }, 
            {
                "mtDocTypeCd": "CIF", 
                "mtDocCd": "PCIF104", 
                "mtDocCdDscp": "组织机构代码证", 
                "mtDocCatCd": "CP", 
                "refId": "fd428a99b5734179939debc027f1b681", 
                "required": "N"
            }
        ]
    }, 
    "cif": {
        "moduleName": "企业信息", 
        "description": "", 
        "modules": {
            "corporate": {
                "moduleName": "客户信息", 
                "description": null, 
                "fields": [
                    {
                        "fieldName": "公司名称", 
                        "fieldAttr": "nm", 
                        "fieldType": "SYS", 
                        "fieldInfo": {
                            "option": "required", 
                            "editor": "N", 
                            "area": null, 
                            "type": null, 
                            "placeholder": null, 
                            "maxLength": null, 
                            "width": null, 
                            "defaultValue": null, 
                            "pattern": null, 
                            "errMsg": null, 
                            "regExp": null
                        }
                    }
                ]
            }, 
            "taxInfo": {
                "moduleName": "工商税务信息", 
                "description": null, 
                "fields": [
                    {
                        "fieldName": "注册日期", 
                        "fieldAttr": "dtRegistered", 
                        "fieldType": "SYS", 
                        "fieldInfo": {
                            "option": "required", 
                            "editor": "N", 
                            "area": null, 
                            "type": null, 
                            "placeholder": null, 
                            "maxLength": null, 
                            "width": null, 
                            "defaultValue": null, 
                            "pattern": null, 
                            "errMsg": null, 
                            "regExp": null
                        }
                    }
                ]
            }, 
            "feature": {
                "moduleName": "特色信息", 
                "description": null, 
                "fields": [ ]
            }
        }
    }, 
    "biz": {
        "moduleName": "经营信息", 
        "description": null, 
        "fields": [
            {
                "fieldName": "开始营业日期", 
                "fieldAttr": "dtCommenceTrading", 
                "fieldType": "SYS", 
                "fieldInfo": {
                    "option": "required", 
                    "editor": "N", 
                    "area": null, 
                    "type": "date", 
                    "placeholder": "时间格式：yyyy-MM-dd", 
                    "maxLength": 10, 
                    "width": null, 
                    "defaultValue": null, 
                    "pattern": "datePicker", 
                    "errMsg": null, 
                    "regExp": null
                }
            }
        ]
    }, 
    "rels": {
        "moduleName": "主要成员", 
        "description": "关联人，有且只能填写一个法人关联人", 
        "modules": {
            "legalRelInfo": {
                "moduleName": "关联信息", 
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
            "identity": {
                "moduleName": "关联人身份信息", 
                "description": null, 
                "fields": [
                    {
                        "fieldName": "关联人姓名", 
                        "fieldAttr": "nm", 
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
                "moduleName": "关联人财务信息", 
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
                "moduleName": "关联人职业信息/经营信息", 
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
    "contact": {
        "moduleName": "联系人信息", 
        "description": null, 
        "fields": [
            {
                "fieldName": "姓名", 
                "fieldAttr": "nm", 
                "fieldType": "SYS", 
                "fieldInfo": {
                    "option": "required", 
                    "editor": "Y", 
                    "area": null, 
                    "type": "input", 
                    "placeholder": null, 
                    "maxLength": 100, 
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


```
[接口完整字段配置](cp_fafc_field_all_config.md)
## FAQ
关于此文档暂时还没有FAQ