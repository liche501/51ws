1. **用户通过短信登陆（注册）**

- 弹iOS的使用用户数据、网络等，确认框。

- 输入手机号码。

- 点击发送验证码按钮，用正则验证是否为电话号

  — 验证电话号失败：弹message框（请输入正确的电话号）

  — 验证电话号成功：调用**短信发送接口**。

  ​		— 调用短信发送接口成功：弹message框（内容：短信发送成功），并倒计时60秒（按钮变成倒计				时按钮，不可点击）

  ​		— 调用短信发送接口失败：弹message框（内容：短信发送失败，请重新发送）

    — 倒计时60秒结束后，按钮变成“**重新发送**”。

- 点击用户协议，弹出用户协议页面（从右到左弹出）

- 点击登陆按钮

  — 未输入电话号时，弹message框（内容：请输入电话号）

  — 未输入短信验证码，弹message框（内容：请输入短信验证码）

  — 未勾选“以阅读并同意51WS用户协议”，弹message框（内容：请勾选用户协议）

  — 满足以上3个条件，调用**<u>验证短信（登陆／注册）接口</u>**

  ​	— 调用成功：跳转的首页

  ​	— 调用失败：弹message框（内容：登陆失败，请重试）

2. 进入首页。

- ​	调用**<u>获取用户通用数据接口</u>**，根据返回结果的**mainNotice**字段判断是否要弹公告。

​	(mainNotice不空时，弹alert，显示公告)

3. 弹授权摄像头，确认框。
4. 导航条左上有菜单。

- ​	调用**<u>消息List接口</u>**，有未读的消息时，显示小红点（需要在app端，保存消息是否读过的状态，来显示小红点）。

5. 点击扫描按钮，调转到扫描的页面。

6. 点击左上角菜单，打开菜单（打开方式：从右到左）。

   -  用户账号（显示电话号）。


   - 我的图片。

     ​	— 点击跳转**我的照片**页面。

     ​	— 调用获取用户通用数据接口，根据返回结果的imageUrl字段，显示图片。

- 帮助与反馈。

  ​	— 扫描时候的使用方法。

  ​	— 如何处理扫描异常。

  ​	— 意见反馈。

  ​	— 客服电话。

- 消息。


- 当前版本。


- 退出登陆，弹confirm框，确认。（删除本地保存的token，跳转到登陆页面）。



1. 点击首页的扫描按钮，跳转到扫描页面

   -  显示扫描的特效（一条横线从上往下反复移动）


   - 将图片放入图框内，即可自动扫描


   - 识别图片并后台播放音乐。

     ​	— 识别图片成功：调用**<u>获取用户通用数据接口</u>**，根据返回结果的**fileUrl**字段,下载声音，播放。

     ​	— 显示播放声音的loadingbar，声音一般10秒左右

     ​	— 播放声音时扫描的特效隐藏。

     ​	— 声音播放完毕，再显示扫描的特效。

     ​	— 点击返回按钮，立即中断播放声音。

- 20秒没有识别出来，谈message框（内容：尚未扫描到图片，请对准图片）。



说明：

1. 用object-c语言开发。
2. 后端api，ui，素材，我们提供。
3. 验证图片功能需用，easyAr sdk开发。
