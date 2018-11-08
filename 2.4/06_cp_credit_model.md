#获取企业定性评分模型接口
## 描述
授信申请前获取企业定性评分
具体方法详见<a href="https://codeload.github.com/lianjintai/openapi-demo-java/zip/master" target="_blank">接口demo下载</a>获取企贷定性打分demo,包路径[com.ljt.openapi.demo.demos.CpCreditModelDemo.java]。


## API代码
loan\_app:cp\_app:credit\_model


## 请求参数
| 名称 | 类型 | 是否必须 | 描述 | 示例值 |
| --- | --- | --- | --- | --- |
| mtIndDetailCd | String | 是 | 行业小类 | a0111 |
| employeeCnt | BigDecimal | 是 | 从业人数(单位：人) | 1000 |
| saleAmt | BigDecimal | 否 | 营业收入(单位：万元) | 12358.56 |
| assetAmt | BigDecimal | 是 | 资产总额(单位：万元) | 403029.23 |
| dtRegistered | Date | 是 | 注册时间 | 2017-05-03 15:12:24 |



## 响应参数
| 名称 | 类型 | 描述 |示例值 |
| --- | --- | --- | --- |
| mtCpCreditModelCd | String |  信用指标模型cd | N1 |
| outerModelId | String |  外部模型代码 | 10000032664817 |
| mtCpCreditModelIndexList | List | 信用指标模型集合 | [信用指标模型信息](#信用指标模型信息) | 

#### 信用指标模型信息
| 名称 | 类型 | 描述 |示例值 |
| --- | --- | --- | --- |
| cd | String |  企业信用指标模型指标cd | chhfw |
| dscp | String |  企业信用指标模型指标 | 产品或服务优势 |
| required | String |  是否必填,Y或N | Y |
| maxSelect | String |  最多可选择个数 | 1 |
| options | List |  选项集合 |  [选项集合信息](#选项集合信息)  |

#### 选项集合信息
| 名称 | 类型 | 描述 |示例值 |
| --- | --- | --- | --- |
| cd | String |  企业信用指标模型指标选项cd | A/B/C |
| dscp | String |  企业信用指标模型指标选项 | 远超同业/良好/一般水平 |

## 错误码

## 示例
### 请求示例
```javascript
{
    "mtIndDetailCd": "a0111", 
    "employeeCnt": 1000, 
    "saleAmt": 12358.56, 
    "assetAmt": 403029.23, 
    "dtRegistered": "2017-05-03 15:12:24"
}
```
### 返回示例
```javascript
{
    "mtCpCreditModelCd": "N1", 
    "outerModelId": "10000032664817", 
    "mtCpCreditModelIndexList": [
        {
            "cd": "chhfw", 
            "dscp": "产品或服务优势", 
            "required": "Y", 
            "maxSelect": "1", 
            "options": [
                {
                    "cd": "A", 
                    "dscp": "远超同业"
                }, 
                {
                    "cd": "B", 
                    "dscp": "良好"
                }, 
                {
                    "cd": "C", 
                    "dscp": "一般水平"
                }, 
                {
                    "cd": "D", 
                    "dscp": "低于同业"
                }
            ]
        }, 
        {
            "cd": "cwgl", 
            "dscp": "财务管理规范性", 
            "required": "Y", 
            "maxSelect": "4", 
            "options": [
                {
                    "cd": "A", 
                    "dscp": "有完善的财务制度"
                }, 
                {
                    "cd": "B", 
                    "dscp": "有独立的财务部门，有专职会计和出纳人员"
                }, 
                {
                    "cd": "C", 
                    "dscp": "报表质量高"
                }, 
                {
                    "cd": "D", 
                    "dscp": "有专职的财务经理和财务负责人（除主管财务工作外不承担其他工作职能）"
                }
            ]
        }
    ]
}
```
## FAQ
关于此文档暂时还没有FAQ