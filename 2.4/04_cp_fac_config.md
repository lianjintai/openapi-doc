#获取企贷产品配置	

## 描述
仅支持企业贷款，包括企贷字段配置、需要上传申请材料列表、阿里云OSS令牌

## API代码
loan_app:cp_fac:config

## 示例代码
具体方法详见<a href="https://codeload.github.com/lianjintai/openapi-demo-java/zip/master" target="_blank">接口demo下载</a>,包路径[	com.ljt.openapi.demo.demos.CreditAppCpFacConfDemo]。


## 请求参数
| 名称 | 类型 | 是否必须 | 描述 | 示例值 |
| --- | --- | --- | --- | --- |
| mtFacCd | String | 是 | 贷款产品业务CD | 1010 |

## 响应参数
| 名称 | 类型 | 描述 |示例值 |
| --- | --- | --- | --- |
| cif | json | 授信时“客户信息”所需要的数据字段及格式 [模块](#模块)|  |
| biz | json | 授信时“经营信息”所需要的数据字段及格式 [模块](#模块)|  |
| rels | json | 授信时“主要成员”所需要的数据字段及格式 [模块](#模块)| |  
| contact | json | 授信时“主要成员中”联系人所需要的数据字段及格式 [模块](#模块)| |
| fac | json | 授信时“贷款产品”所需要的数据字段及格式 [模块](#模块)| |  
| doc | json | 授信时需要“上传的申请材料”列表和上传申请材料到“阿里云OSS”的密钥 [申请材料](#申请材料) | ||  

### 模块
| 名称 | 类型 | 描述 |示例值 |
| --- | --- | --- | --- |
| moduleName | String | 模块名称 |  |
| description | String | 描述模块具体做什么，有什么规则等详细说明 |  |
| fields | JSON(List) | 模块包含的字段列表 [字段](#字段)|  |
| modules | JSON(List) | 模块包含的子模块列表 同“fileds”字段只存在一个。 [模块](#模块) |  ||


### 字段
| 名称 | 类型 | 描述 |示例值 |
| --- | --- | --- | --- |
| fieldName | String | 字段中文名称 |  |
| fieldAttr | String | 字段name，授信时传入的参数名 |  |
| fieldType | String | 字段类型，SYS:系统，CUSTOM：自定义字段 |  |
| fieldInfo | JSON | [字段属性](#字段属性) |  ||

### 字段属性
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
| regExp | String | 校验正则表达式 |  ||

### 申请材料
| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| url | Json | 是 |  | oss上传密钥 [oss上传密钥](#oss上传密钥) |  |
| docs | Json(list) | 是 |  | 申请材料列表 [业务上传申请材料列表](#业务上传申请材料列表) |  ||


#### oss上传签名密钥
| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| accessid | String | 是 | 20 |  |  |
| policy | String | 是 | 20 |  |  |
| signature | String | 是 | 20 |  |  |
| dir | String | 是 | 20 |  |  |
| host | String | 是 | 20 |  |  |
| callback | String | 是 | 20 |  |  ||

#### 业务上传申请材料列表 
| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| mtDocTypeCd | String | 是 | 20 | 申请材料门类Cd, CIF:客户申请材料，FAC：业务申请材料|  |
| mtDocCd | String | 是 | 20 |   申请材料Cd，在上传申请材料的时候需要使用 ||
| mtDocCdDscp | String | 是 | 20 | 申请材料描述 |  |
| mtDocCatCd | String | 是 | 20 | 申请材料大类Cd |  |
| refId | String | 是 | 20 | 申请材料关联ID，在上传申请材料组织文件的时候，不同的申请材料门类，使用的refId不同。在授信申请的时候需要将申请材料门类为“CIF”的refId放入"doc.cifDocRefId"值中,门类为"FAC"的refId放入"doc.facDocRefId"值中 | |
| required | String | 是 | 20 |  是否必须，Y是，N不是 |  ||

## 错误码
| 描述 | HTTP状态码 | 语义 |
| --- | --- | --- | 
| acctNo未找到 | 400 | 请输入正确的appId,或检查申请类型与申请ID是否匹配 ||

## 请求参数示例
```javascript
{
    "mtFacCd":"1010"
}
```
## 返回示例
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
##产品可配置所有字段

 [企贷-产品可配置所有字段](cp_fac_all_config.md)
 
## FAQ
关于此文档暂时还没有FAQ

1、影响授信的审批具体意思
>申请申请创建企贷贷的时候，如果业务要求必传入部分没有填写内容，则需要登陆我们的管理系统补充填写信息，然后继续再将企贷贷申请提交审批。

2、怎样才能授信的审批
>填写业务需要必传的信息。然后提交推送贷款信息给“资金方”或“担保方”->“资金”完成授信审批
