#银行交易流水保存
## 描述
借款人为企业时，可以在融资申请推送前上传交易流水信息，炼金台会分析上传的交易流水，以便资方对借款人的资质进行更客观的审核。 请知悉以下两点： 1.如果同一个申请上传多次相同的交易流水（交易流水号相同）时，最后上传的交易流水会覆盖之前的。 2.删除交易流水文件时，文件中包含的流水也会被删除（两个文件中包含同一个交易流水，a.删除第一次上传的文件时，交易流水不会被删除；b.删除第二次上传的文件时，交易流水同时被删除，不会还原第一次上传的交易流水）。

## API代码
loan\_app:deposit\_acct\_trxns:save 

## 请求参数
| 名称 | 类型 | 是否必须 | 描述 | 示例值 |
| --- | --- | --- | --- | --- |
| appId | String | 是 | 申请ID（[融资申请创建API](20_app_push.md)返回的结果） | 1ba41a90dedc4878b930b30fc3ba149d |
| mtFinInsttnCd | String | 是 | 所属银行代码，具体详见[附件](../3_附件.md) | 01 |
| items | JSON(List) | 是 | 交易流水明细，具体详见[交易流水明细](#交易流水明细) |

### 交易流水明细
| 名称 | 类型 | 是否必须 | 最大长度 | 描述 | 示例值 |
| --- | --- | --- | --- | --- | --- |
| acctNo | String | 是 | 25 | 存款账号 | 6217002710000684874 |
| acctNm | String | 是 | 80 | 存款账户名称 | 北京海恩炼鑫台信息技术有限责任公司 |
| dtTrxn | datetime | 是 | 0 | 交易日期 | 2017\-03\-18 13:00:00 |
| debitAmount | Number | 是 | (16,4) | 借方发生额 | 3000 |
| creditAmount | Number | 是 | (16,4) | 贷方发生额 | 0 |
| balance | Number | 是 | (16,4) | 余额 | 780579.09 |
| mtCurCd | String | 是 | 20 | 币种 | 人民币 |
| toAcctNo | String | \- | 50 | 对方账号 | 622200020011111111 |
| toAcctNo | String | \- | 80 | 对方户名 | 董强 |
| toBankNm | String | \- | 80 | 对方开户机构 | 中国工商银行股份有限公司北京西客站支行 |
| dtAccounting | Date | 是 | 0 | 记账日期 | 2017\-03\-18 |
| summary | String | \- | 300 | 摘要 | 自定义 |
| remark | String | \- | 300 | 备注 | 置换补贴 |
| serialNo | String | \- | 50 | 交易流水号 | 6394-1108637000NDPB2D8VM |

- 交易流水明细示例
```javascript
{
	"items": [
		{
			"acctNo":"6217002710000684874",
			"acctNm":"北京海恩炼鑫台信息技术有限责任公司",
			"dtTrxn":"2017-03-18 13:00:00",
			"debitAmount":"3000",
			"creditAmount":"0",
			"balance":"780579.09",
			"mtCurCd":"人民币",
			"toAcctNm":"董强",
			"toAcctNo":"622200020011111111",
			"toBankNm":"中国工商银行股份有限公司北京西客站支行",
			"dtAccounting":"2017-03-18",
			"summary":"自定义",
			"remark":"置换补贴",
			"serialNo":"6394-1108637000NDPB2D8VM"
		}
	]
}
```

## 响应参数
| 名称 | 类型 | 描述 |示例值 |
| --- | --- | --- | --- |
| fail | String | 失败条数 | 0 |
| total | String | 保存的交易流水总条数 | 1 |
| appId | String | 申请ID | 1ba41a90dedc4878b930b30fc3ba149d |

## 错误码
| 描述 | HTTP状态码 | 语义 |
| --- | --- | --- | 
| appId未找到 | 400 | 请输入正确的appId |

## 示例
### 请求示例
```javascript
{
	"appId":"1ba41a90dedc4878b930b30fc3ba149d",
	"mtFinInsttnCd":"01",
	"items":[
		{
			"acctNo":"6217002710000684874",
			"acctNm":"北京海恩炼鑫台信息技术有限责任公司",
			"dtTrxn":"2017-03-18 13:00:00",
			"debitAmount":"3000",
			"creditAmount":"0",
			"balance":"780579.09",
			"mtCurCd":"人民币",
			"toAcctNm":"董强",
			"toAcctNo":"622200020011111111",
			"toBankNm":"中国工商银行股份有限公司北京西客站支行",
			"dtAccounting":"2017-03-18",
			"summary":"自定义",
			"remark":"置换补贴",
			"serialNo":"6394-1108637000NDPB2D8VM"
		}
	]
}
```
### 返回示例
```javascript
{
	"fail":0,
	"total":1,
	"appId":"1ba41a90dedc4878b930b30fc3ba149d"
}
```
## FAQ
关于此文档暂时还没有FAQ
