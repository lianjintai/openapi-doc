#授信自动审批接口
## 描述
将授信数据通过接口实现自动审批功能,省去人工审批（暂时只支持个贷）
具体方法详见<a href="https://codeload.github.com/lianjintai/openapi-demo-java/zip/master" target="_blank">接口demo下载</a>授信自动审批demo,包路径[com.ljt.openapi.demo.demos.LoanAppAutoActDemo]。


## API代码
loan\_app:app:auto\_act

## 请求参数
| 名称 | 类型 | 是否必须 | 描述 | 示例值 |
| --- | --- | --- | --- | --- |
| appID | String | 是 | 申请ID | c4d6f8cfabc547539c2ae4fb49130aff |




## 响应参数
| 名称 | 类型 | 描述 |示例值 |
| --- | --- | --- | --- |
| appID | String | 申请ID | c4d6f8cfabc547539c2ae4fb49130aff |
 

## 错误码

## 示例
### 请求示例
```javascript
{
    "appID": "c4d6f8cfabc547539c2ae4fb49130aff" 
}
```
### 返回示例
```javascript
{
   "appID": "c4d6f8cfabc547539c2ae4fb49130aff"
}
```
## FAQ
关于此文档暂时还没有FAQ