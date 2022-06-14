# SSA
**学习通座位签到、预约、退座、暂离等等**

> 现在，你可以搜索微信号“**heydoone**”更加快捷地使用接口的功能（[需要联系我获得使用资格][1]）
> 
> 接口免费使用。

# API（<a href="#pgjj" color=#00f>苹果捷径</a>）

请求URL为：

*  签到：https://api.nvidia.fun/sign
*  退座：https://api.nvidia.fun/signback
*  暂离：https://api.nvidia.fun/leave
*  取消：https://api.nvidia.fun/cancel

验证码深度学习感谢以下项目的支持

* **dee1024 & kenvifire：https://github.com/dee1024/pytorch-captcha-recognition**
* **PJDong：https://github.com/pprp/captcha_identify.pytorch**

## 签到

``` python
 # 请求地址:https://api.nvidia.fun/sign
 # 请求方法:post
 # 请求参数:
{
    "phonenums": "手机号",
    "key":"密码"
}

 # response
{
    "msg": "不在签到时间内无法签到",
    "value": "True"
}
```

## 离开、退座和取消

* 使用方法与签到一致，离开、退座和取消分别把url上的"sign"替换成"leave"、"signback"和"cancel"即可~

## <a id="pgjj">苹果捷径</a>

* 从url获取内容，url填上你要请求的地址，请求方式选择post，添加两个文本值，详细看下方图片**注意替换为新URL地址！**。
![快捷指令](https://raw.githubusercontent.com/Doone-skser/SSA/main/reference.png)
* 获取字典值，获取"msg"的值
* 显示提醒，将msg的值显示在弹窗。

  [1]: https://www.nvidia.fun/index.php/start-page.html
