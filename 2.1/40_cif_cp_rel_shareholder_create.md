# 创建企业关联
## 描述
与借款人相关的企业（可以调用多次，创建多个关联人），如：
当借款人为个人时，借款人的持股公司等
当借款人为企业时，借款企业的子公司、股东等

## API代码
loan\_app:cif\_cp\_rel:create

## 请求参数
| 名称 | 类型 | 是否必须 | 描述 | 示例值 |
| --- | --- | --- | --- | --- |
| appId | String | 是 | 申请ID（[融资申请创建API](20_app_push.md)返回的结果） | 0092728480d24f |
| base64OfFile | String | 是 | 将文件使用BASE64编码 | |
| mtFinRptCatCd | String | 是 | 财务报表范围代码（1-本部报表、2-合并报表） | 1 |
| mtFinRptTypCd | String | 是 | 财务报表类型代码（1-年报、2-季报、3-月报、4-半年报） | 1 |
| mtFinStsCd | String | 是 | 财务报表状态代码（001-已审计、002-未审计） | 001 |
| dtFin | Date | 是 | 财务报表截止日期（财务报表类型对应范围内的任意日期） | 2017-05-03 15:12:24 |

## 响应参数
| 名称 | 类型 | 描述 |示例值 |
| --- | --- | --- | --- |
| appId | String | 申请ID | 0092728480d24f5d87bf63639b5cfe1c |

## 错误码
| 描述 | HTTP状态码 | 语义 |
| --- | --- | --- | 
| appId未找到 | 400 | 请输入正确的appId |

## 示例
### 请求示例
```javascript
{
    "appId":"0092728480d24f5d87bf63639b5cfe1c",
	"base64OfFile":"dfdasfdsaf2f2f2f2511dasfsdfsdfsdffdsdfafsdf10190dafffb4863168ec04==",
	"mtFinRptCatCd":"1",
	"mtFinRptTypCd":"1",
	"mtFinStsCd":"001",
	"dtFin": "2017-05-03 15:12:24"
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