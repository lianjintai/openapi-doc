#可上传申请材料
## 描述
根据appId查询可上传申请材料列表，需要按照本接口的返回结果，组织申请材料压缩包（见[申请材料压缩包结构](#申请材料压缩包结构)），然后上传申请材料，具体上传方法详见申请材料上传demo。

## API代码
loan\_app:doc:can_upload

## 请求参数
| 名称 | 类型 | 是否必须 | 描述 | 示例值 |
| --- | --- | --- | --- | --- |
| appId | String | 是 | 申请ID（[融资申请创建API](20_app_push.md)返回的结果） | 0092728480d24f5d8 |

## 响应参数
| 名称 | 类型 | 描述 |示例值 |
| --- | --- | --- | --- |
| appId | String | 申请ID | 0092728480d24f5d8 |
| url | String | 文件上传参数（带有授权信息，半小时后失效），见[申请材上传参数](#申请材上传参数)||
| docs | JSON（List） | 申请材料列表（多个），见[申请材料信息](#申请材料信息) |  |

### 申请材料信息
| 名称 | 类型 | 描述 |示例值 |
| --- | --- | --- | --- |
| mtDocTypeCd | String | 申请材料大类 | CIF-客户，COLL-担保，FAC-业务 |
| mtDocCd | String | 申请材料代码|  |
| mtDocCatCd | String | 申请材料小类 | CS:借款人申请材料,CS_BIZ:个体工商户/私营主申请材料,CS_SPOUSE:借款人配偶申请材料,CP:借款企业申请材料,CP_LEGAL_PERSON:借款企业法人申请材料 |
| refId | String | 关联资源ID（根据mtDocTypeCd决定具体关联的资源是什么） |  |
| refName | String | 关联资源名称（根据mtDocTypeCd决定具体关联的资源是什么） |  |
| isNecessary | String | 是否必须上传 | Y，N |

### 申请材上传参数
| 名称 | 类型 | 描述 |
| --- | --- | --- | 
| accessid | String | 访问凭证 |
| policy | String | 访问秘钥 | 
| signature | String | 签名信息  |
| dir | String | 上传路径  |
| host | String | 上传host |
| callback | String | 回调信息 |


## 错误码
| 描述 | HTTP状态码 | 语义 |
| --- | --- | --- | 
| appId未找到 | 400 | 请输入正确的appId,或检查申请类型与申请ID是否匹配 |

## 示例
### 请求示例
```javascript
{
    "appId":"0092728480d24f5d87bf63639b5cfe1c"
}
```
### 返回示例
```javascript
{
    "appId":"0092728480d24f5d8",
    "url": {
        "accessid": "56eY6ZKl5L+h5oGv",
        "policy": "6K6/6Zeu5Yet6K+B",
        "signature": "ASeuZvneqyIVG2ioJJinZFZCFns=",
        "dir": "doc/",
        "host": "https://ljt-sit-oss.oss-cn-beijing.aliyuncs.com",
        "callback": "5Zue6LCD5Zyw5Z2A"
    },
    "docs":[
        {
            "mtDocTypeCd":"CIF",
            "mtDocCd":"PCIF305",
             "mtDocCatCd":"CS_BIZ",
            "refId":"bf63639b5cfe1c",
            "refName":"北京海恩炼鑫台信息技术有限责任公司",
            "isNecessary":"N"
        },
        {
            "mtDocTypeCd":"CIF",
            "mtDocCd":"PCIF311",
            "mtDocCatCd":"CS",
            "refId":"bf63639b5cfe1c",
            "refName":"北京海恩炼鑫台信息技术有限责任公司",
            "isNecessary":"N"
        },
       {
           "mtDocTypeCd":"CIF",
           "mtDocCd":"PCIF311",
           "mtDocCatCd":"CS_SPOUSE",
           "refId":"bf63639b5cfe1c",
           "refName":"北京海恩炼鑫台信息技术有限责任公司",
           "isNecessary":"N"
       }
    ]
   
}
```

### 申请材料压缩包结构
文件名：{appId}.zip
压缩包内容：
```
{appId}.zip
├── {mtDocCd1} \
│    ├── {refId1} \
│    │      └── {文件1}
│    └── {refId2} \
│           ├── {文件2}
│           └── {文件3}
└── {mtDocCd2} \
     └── {refId3} \
            └── {文件4}
```
## FAQ
关于此文档暂时还没有FAQ