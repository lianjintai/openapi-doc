#账务核对接口
## 描述
平台方每天凌晨1:00后，可通过本接口查询前一日的交易流水列表（包括放款、还款、冲正等涉及余额金融交易）
主要用途：防止前一日的日间交易处理过程中出现差错，没有及时发现和处理。一旦出现差错需在下一工作日内联系炼金台的对接专员进行检查。
备注：前一日未发生金融交易时，返回空报文。

## API代码
loan\_app:account:check


## 请求参数
不需要请求参数


## 响应参数
| 名称 | 类型 | 描述 |示例值 |
| --- | --- | --- | --- |
| contractNo | String |  合同编号 |  |
| acctNo | String |  贷款账号 |  |
| counterpartyAcctNo | String |  交易对手账号 |  |
| dtTrxn | Date | 交易时间 | 2017-04-05 13:22:39 |
| trxnNo | String | 交易流水号（当日不重复） | |  
| mtTrxnTypeCd | String | 交易类型代码 | |  
| trxnAmt | Number | 交易金额 | |  
| outstdAmt | Number | 账户余额 | |  
| remark | String | 交易备注 | |  |

## 错误码

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
    "mt_app_sts_cd":"APPROVED"
}
```
## FAQ
关于此文档暂时还没有FAQ