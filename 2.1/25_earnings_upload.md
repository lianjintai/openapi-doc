#企业财报上传
## 描述
借款人为企业时，可以在融资申请推送前上传财报信息，炼金台会根据财报的情况对客户进行信用评级，以便资方对借款人的资质进行更客观的审核。
请知悉以下两点：
1.如果同一个申请上传多次相同的财报（财报范围、类型、状态、年份、月份相同）时，最后上传的财报会覆盖之前的。
2.申请状态为已推送、已批准时允许上传新的财报，但不会推送给资金方，也不会影响本次的评分结果，只会在下次申请时推送给资金方并更新评分结果。
## 财报模版
<a href="https://dcms.lianjintai.com/static/downloads/finance/%E7%B3%BB%E7%BB%9F07%E7%89%88%E4%BC%81%E4%B8%9A%E8%B4%A2%E5%8A%A1%E6%8A%A5%E8%A1%A8.xlsx" target="_blank">07版财报模版</a>,
<a href="https://dcms.lianjintai.com/static/downloads/finance/%E7%B3%BB%E7%BB%9F05%E7%89%88%E4%BC%81%E4%B8%9A%E8%B4%A2%E5%8A%A1%E6%8A%A5%E8%A1%A8.xlsx" target="_blank">05版财报模版</a>

## API代码
loan\_app:earnings:upload 

## 请求参数
| 名称 | 类型 | 是否必须 | 描述 | 示例值 |
| --- | --- | --- | --- | --- |
| appId | String | 是 | 申请ID（[融资申请创建API](20_app_push.md)返回的结果） | 0092728480d24f |
| base64OfFile | String | 是 | 将文件使用BASE64编码 | |
| mtFinRptCatCd | String | 是 | 财务报表范围代码（1-本部报表、2-合并报表） | 1 |
| mtFinRptTypCd | String | 是 | 财务报表类型代码（1-年报、2-季报、3-月报、4-半年报） | 1 |
| mtFinStsCd | String | 是 | 财务报表状态代码（001-已审计、002-未审计） | 001 |
| dtFin | Date | 是 | 财务报表截止日期（财务报表类型对应范围内的任意日期） | 2017-05-03 |

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
	"dtFin": "2017-05-03 "
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