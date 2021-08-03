# 用户交互

用户可以通过网页和聊天发消息与机器人进行交互。

### 网页交互

用户可通过以下 4 种方式直接打开机器人主页进行网页交互

- 首页超级入口

  Telegram、Facebook Messenger、微信这些聊天软件都支持机器人（小程序）的功能，作为基础聊天功能的延伸都非常重视，Mixin 更进一步把首页导航菜单的权利交给用户，把一级入口留给机器人开发者，用户可以把自己最喜欢、最常用的机器人置顶到首页，而机器人作为一级入口也将获得用户更多使用频率和时长。
  
  ![长按并拖拽](./user-interaction-drag.png)

  用户可通过长按拖拽置顶显示到首页底部菜单，用户从首页底部点图标会直接打开机器人首页。
  
  **从 0.28.0 版本开始首页底部菜单支持 3 个机器人置顶（之前的版本支持 2 个）。**

- 聊天底部菜单

  ![点击底部机器人图标](./user-interaction-chat-bot.png)

  当用户打开机器人的会话界面后，点底部机器人图标可直接打开机器人首页。

- 聊天左下角菜单

  ![点击聊天左下角 + 菜单](./user-interaction-chat-menu.png)

  当机器人被添加为群组成员或被用户设置为分享的机器人，进入会话点左下角菜单就会显示出来，点击图标会直接打开机器人首页。

- 机器人弹窗

  ![点击个人用左下角机器人图标](./user-interaction-profile.png)

  机器人个人页点左下角机器人图标也会直接打开机器人首页。


### 聊天窗口交互

从首页聊天列表点机器人或者从机器人弹窗点会话将进入聊天窗口交互模式，通常用户会留言问问题，机器人可以自动或者人工回复文字、图片、卡片等消息反馈给用户。用户第一次打开与机器人的聊天窗口会显示如下提示：

![欢迎](./user-interaction-welcome.png)

点「打开主页」按钮会直接打开机器人主页，点「打招呼」会给机器人发送一条 `Hi` 文字消息。

- 被动回复

  当用户添加当前机器人为联系人时，机器人会收到系统帮用户发的一条消息"你好"，机器人应该回复关于机器人的介绍，并引导用户如何使用。可以给用户回复一段文字 + 一个或多个按钮，一点按钮就能打开机器人主页或者回复用户更多介绍信息，例如：

  ![添加机器人](./user-interaction-add-bot.png)

  当用户遇到问题给机器人留言时，机器人应该设置一些关键字自动回复，关键字无法回复的应该自动转发给客服或者开发者，以便进行人工回复，帮用户解决使用问题。

  ![回复](./user-interaction-reply.png)

  机器人 Team Mixin 7000 是 Mixin Messenger 的官方客服机器人，如果用户有使用问题可以直接留言，也可以发送"下载"关键字获得自动回复内容。

- 主动推送

  机器人可以推送重要的通知给用户，例如新的活动或者公告：

  ![通知](./user-interaction-notice.png)

  如果内容比较短建议推送文字消息，如果内容较长，建议推送 POST 文章消息，支持 markdown 格式，可以把 markdown 内容发送给 7000103014 机器人转成 POST 文章消息格式。
  

- 指令交互

  支持指令交互很酷，但让用户输入指令门槛有点高，将 APP_BUTTON 的 action 按格式 `input:SOMETHING` 设置就能获得点击按钮自动发消息的能力，非常实用。例如当前的 App Button 的 action 是 input:subscribe ，当用户点击这个按钮时客户端会自动发送一条 subscribe 的消息给机器人，开发者可以任意指定 input 后面的文字。

  ![指令交互](./user-interaction-cmd.png)

  上述 4 个按钮的 action 分别指定为 `input:8 A`、`input:8 B`、`input:8 C`、`input:8 D`，当用户点击按钮时，客户端会自动帮用户发送 `8 A`、`8 B`、`8 C`、`8 D` 的指令。