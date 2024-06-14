# chatgpt-web
Pure Javascript ChatGPT demo based on Azure OpenAI API 

纯JS实现的ChatGPT项目，基于Azure OpenAI API

部署一个HTML文件即可使用。

支持复制/更新/刷新会话，语音输入，朗读等功能，以及众多[自定义选项](#自定义选项)。

支持搜索会话，深色模式，自定义头像，快捷键，多语言，[环境变量](#环境变量)，[PWA应用](#pwa应用)，API额度显示等。

支持[加密HTML文件](#加密html文件)。

参考项目: 
[markdown-it](https://github.com/markdown-it/markdown-it), 
[highlight.js](https://github.com/highlightjs/highlight.js), 
[github-markdown-css](https://github.com/sindresorhus/github-markdown-css), 
[chatgpt-html](https://github.com/slippersheepig/chatgpt-html), 
[markdown-it-copy](https://github.com/ReAlign/markdown-it-copy), 
[markdown-it-texmath](https://github.com/goessner/markdown-it-texmath), 
[awesome-chatgpt-prompts-zh](https://github.com/PlexPt/awesome-chatgpt-prompts-zh)

![示例](https://raw.githubusercontent.com/xqdoo00o/chatgpt-web/main/example.png)

## Demo

[在线预览](https://xqdoo00o.github.io/chatgpt-web/) （使用需配置OpenAI接口和API密钥）

## 使用方法

直接把项目丢进web服务器里，访问index.html。

## PWA应用
部署文件[icon.png](https://raw.githubusercontent.com/xqdoo00o/chatgpt-web/main/icon.png)，[manifest.json](https://raw.githubusercontent.com/xqdoo00o/chatgpt-web/main/manifest.json)，[sw.js](https://raw.githubusercontent.com/xqdoo00o/chatgpt-web/main/sw.js)到index.html同目录下，即可支持PWA应用。

**注意：如果重命名index.html使用，则sw.js文件中`./index.html`也需修改。**

**部署PWA应用后，更新html文件需同步更新sw.js，不然无法更新成功。**

## 自定义选项

- 左边栏支持，搜索会话，新建/重命名/删除(会话/文件夹)，中英双语，浅色/深色/自动主题模式，导出/导入/重置会话和设置数据，快捷键，显示API额度，显示本地存储。

- 自己输入API终结点和对应的密钥。模型名称基本没啥用，空着。

- 可选用户头像，可修改为任意图片地址。

- 可选系统角色，默认不开启，有四个预设角色，并动态加载[awesome-chatgpt-prompts-zh](https://github.com/PlexPt/awesome-chatgpt-prompts-zh)或[awesome-chatgpt-prompts](https://github.com/f/awesome-chatgpt-prompts)中的角色。

- 可选角色性格，默认灵活创新，对应接口文档的top_p参数。

- 可选回答质量，默认平衡，对应接口文档的temperature参数。

- 修改打字机速度，默认较快，值越大速度越快。

- 可选连续会话上下文信息限制，默认25条，对话中包含上下文信息，会导致api费用增加。设置为0条则关闭连续会话。

- 允许长回复，默认关闭，**开启后可能导致api费用增加，并丢失全部上下文，对于一些要发送`继续`才完整的回复，不用发`继续`了。**

- 选择语音，默认Bing语音，支持Azure语音和系统语音，可分开设置提问语音和回答语音。

- 音量，默认最大。

- 语速，默认正常。

- 音调，默认正常。

- 允许连续朗读，默认开启，连续郎读到所有对话结束。

- 允许自动朗读，默认关闭，自动朗读新的回答。**iOS需打开设置-自动播放视频预览，Mac上Safari需打开此网站的设置-允许全部自动播放**

- 支持语音输入，默认识别为普通话，可长按语音按钮修改识别语言选项。**语音识别必需条件：使用chrome内核系浏览器 + https网页或本地网页，允许网页的麦克风权限，并已安装麦克风设备。** 

- 自动发送关键词，默认为空，识别到关键词后自动发送。

- 自动停止关键词，默认为空，识别到关键词后自动停止识别。

- 自动发送延迟时间，默认为0秒，即不自动发送。不为0秒时，表示识别到内容后，自动发送延迟的时间。

- 保持监听，默认关闭，保持麦克风一直处于监听状态，除非识别报错或手动关闭识别。

## 加密HTML文件

使用[加密网页](https://xqdoo00o.github.io/chatgpt-web/encrypt.html)可加密index.html文件。

- 密码，打开加密HTML的密码。

- 是否压缩，默认允许，较大HTML可减少加密后文件体积。

- 允许记住密码，默认允许，是否允许前端记住密码。

- 记住密码有效期，默认永不过期，过期后需重新输入密码。

- 拷贝index.html内容到要加密的HTML文本框，点击生成按钮后，即可下载加密HTML，并替换index.html使用。

**注意：该方式仅加密前端HTML，不加密OpenAI反代接口。**

**可取消OpenAI反代接口的默认API密钥，打开[index.html代码](https://github.com/xqdoo00o/chatgpt-web/blob/main/index.html#L2840)，此行结尾添加代码`value="sk-xxx"`，则默认使用该密钥**