## 1. 接口描述
本接口（PayDealsNew）用于支付订单，可以是自付，也可以是代理商代付。
接口请求域名：<font style="color:red">partners.api.qcloud.com</font>


## 2. 输入参数
以下请求参数列表仅列出了接口请求参数，正式调用时需要加上公共请求参数，见 <a href="/doc/api/372/4153" title="公共请求参数">公共请求参数</a> 页面。其中，此接口的 Action 字段为 PayDealsNew。

| 参数名称        | 是否必选 | 类型     | 描述             |
| ----------- | ---- | ------ | -------------- |
| ownerUin    | 是    | Int    | 订单拥有者 uin       |
| agentPay    | 是    | Int    | 代付标志，1：代付；0：自付 |
| dealNames.n | 是    | String | 订单号数组          |


## 3. 输出参数
| 参数名称     | 类型     | 描述                                       |
| -------- | ------ | ---------------------------------------- |
| code     | Int    | 公共错误码, 0表示成功，其他值表示失败。详见错误码页面的 <a href="https://cloud.tencent.com/document/product/563/8082" title="公共错误码">公共错误码</a>。 |
| codeDesc | String | 业务侧错误码。成功时返回 Success，错误时返回具体业务错误原因。       |
| message  | String | 模块错误信息描述，与接口相关。                          |
| data     | Array  | 输出结果，包含支付成功的订单号                          |

其中，data参数的构成如下：

| 参数名称        | 类型    | 描述               |
| ----------- | ----- | ---------------- |
| dealNames   | Array | 支付成功的订单号数组       |
| resourceIds | Array | 支付成功的订单对应的资源 ID 数组 |
| dealIds     | Array | 支付成功的订单对应的自增 ID 数组 |

## 4. 示例

```
https://partners.api.qcloud.com/v2/index.php?
&<公共请求参数>
&ownerUin=xxxx&agentPay=1&dealNames.0=xxxx
```
返回示例如下：
```
{
    "code": 0,
    "message": "",
    "codeDesc": "Success",
    "data": {
        "dealNames": [
            "20161223129073"
        ],
        "resourceIds": [],
        "dealIds": [
            "2982973"
        ]
    }
}
```
