# SSA
**学习通座位签到、预约、退座、暂离、综合信息查询（包含座位楼层位置、所有座位的使用信息、签到地理位置范围等）**

> 现在，你可以关注微信公众号“**杜恩**”或者搜索微信号“**heydoone**”更加快捷地使用接口的功能。
> <br>**不同学校的数据格式有些许的不同，可以在Issues提交你的问题，我会尽力解决的。**

# 微信公众号现在已经开放测试

 需要联系我通过一下的任何方式发送你的**房间ID**以及**开始预约第二天座的时间**：

* QQ：1921868580
* Email：admin@nvidia.fun

**前提：你需要先在公众号绑定你的账号且能查询至少一次的预约记录（这一步是为了验证预约系统是否为新版）**

## 目录

* <a href="#p1"><font size=2 color=#00f>公众号更新日志</font></a><br>
* <a href="#p2"><font size=2 color=#00f>微信公众号使用教程</font></a><br>
* <a href="#p3"><font size=2 color=#00f>接口更新日志</font></a><br>
* <a href="#pgjj"><font size=2 color=#00f>苹果捷径简单教程</font></a><br>

## <a id="p1">公众号更新日志</a>

### 2022年3月29日

* 修复了无滑动验证码预约只能预约前两个小时的问题。
* 修复了时间切片的问题。
* 把自动签到的检测间隔修改为1分钟。

### 2022年3月26日

* 自动签到功能已上线，欢迎各位同学前来测试（仅支持新版）。
* 自动退座功能暂缓。

### 2022年3月25日

* 自动签到、自动退座3月26日实装
* 查询的记录缩减到最近6条

### 2022年3月22日

* 支持滑块验证码自动预约

## <a id="p2">微信公众号使用教程</a>

* 首先按提示发送您的手机号加上空格（**必须且只能有一个**）密码紧跟其后即可绑定账号至您的微信唯一标识，若需要修改，则重新发送即可。
* 分别发送**签到**、**暂退**、**查询**、**离开**或**取消**来实现接口的功能。

## <a id="p3">接口更新日志</a> （源代码请看`flask/SSA_flask.py`）

*注意：它只支持最新一期的图书馆预约系统2021年，如果你的学校不适用，**请将所有请求的域名中的seat修改为seatengine并附带seatId的值**再试或者提交issues*

### 2022年3月10日

* 公众号“杜恩”已上线查询功能，发送“查询”可以查询近10条的预约记录，这与之后的预约有关。
* 预约正在测试中，即将在公众号上线。

### 2022年3月8日

* 修复了在多预约的情况下签到失败的问题，现在将之间签到最近待签到的座位。
* 不久后更新老版系统的签到、退座、取消和暂离。
* 不久后开放**预约接口**。

### 2022年3月6日

* 修复了在多预约情况下不能签到的问题。
* 修复了正在学习的座位取消导致上限的问题（建议退座，这样不消耗预约次数。）
* 优化了返回的信息提示，更加人性化啦。

### 2022年3月5日

* 修复了请求返回时显示手机号或者密码的错误提示，但实际已操作。
* 优化了文字提示：成功操作会显示位置已经座位号。

### 部分功能已经开通接口（<a href="#pgjj" color=#00f>苹果捷径使用方法</a>）

#### 签到

``` python
 # 请求地址:https://o.nvidia.fun:12345/sign
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

#### 离开、退座和取消

* 使用方法与签到一致，离开、退座和取消分别把url上的"sign"替换成"leave"、"signback"和"cancel"即可~

## <a id="pgjj">苹果捷径简单教程</a>

* 从url获取内容，url填上你要请求的地址，请求方式选择post，添加两个文本值，详细看下方的请求参数。
* 获取字典值，获取"msg"的值
* 显示提醒，将msg的值显示在弹窗。
