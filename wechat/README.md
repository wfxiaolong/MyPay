<p align="center">
<h3 align="center">MyPay —— 微信支付API</h3><hr>
</p>

```
适用于商户自己的微信端电商平台的支付
移动端微信支付的网页，商户不需要进行额外太多开发，可同步返回和异步返回。
同步返回和异步的参数需要通过后台设置，返回参数同上接口
```


#### 请求:

```
Method: HTTP GET

https://mypay.iemoney.co.nz/wechatApi/wechatPay/$mid/$fee/$trade_no/$memo
```

|Parameter	|Type 	 |Description|
|-----------|--------|-----------|
|mid        |int     |5位数，这边获取注册|
|fee        |string  |最多两位小数的数值，如：200.65|
|trade_no   |string  |商户自己的订单号，32位，官方建议：时间日期，加随机数，唯一订单号|
|memo    |string  |备注|

#### 返回:

* 支付回调：

|Parameter	|Type 	 |Description|
|-----------|--------|-----------|
|trade_no   |string  |商户自己的订单号，32位，官方建议：时间日期，加随机数，唯一订单号|
|trade_status   |string  |订单的支付状态，成功返回“SUCCESS”|
|sign       |string  |签名，签名规则 sign md5($trade_no.$trade_status.$api_key) <br/>api_key 通过平台注册时获取|

```

同步返回：
https://return.url/?trade_no=20180125033932&trade_status=SUCCESS

异步返回：
https://callback.url/?trade_no=20180125033932&trade_status=SUCCESS&sign=04a05e0d54598ef01882c18da7992762

异步请求收到后，要输出"SUCCESS"，不然会一直重复发送异步通知

```
