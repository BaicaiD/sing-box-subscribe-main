
# 一、服务器部署

## 开始使用

1. 点击此项目右上角的 fork 按钮，fork 本项目到自己仓库；
2. 点击右侧按钮开始部署：
   [![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new)，直接使用 Github 账号登录即可；[请查看详细教程](./docs/vercel-cn.md#如何新建项目)。
3. 部署完毕后，即可开始使用；
4. （可选）[绑定自定义域名](https://vercel.com/docs/concepts/projects/domains/add-a-domain)：Vercel 分配的域名 DNS 在某些区域被污染了，绑定自定义域名即可直连。

### 打开自动更新

> 如果你遇到了 Upstream Sync 执行错误，请手动 Sync Fork 一次！

当你 fork 项目之后，由于 Github 的限制，需要手动去你 fork 后的项目的 Actions 页面启用 Workflows，并启用 Upstream Sync Action，启用之后即可开启每小时定时自动更新：

![自动更新](https://github.com/Toperlock/ChatGPT-Next-Web/raw/main/docs/images/enable-actions.jpg)

![启用自动更新](https://github.com/Toperlock/ChatGPT-Next-Web/raw/main/docs/images/enable-actions-sync.jpg)

### 手动更新代码

如果你想让手动立即更新，可以查看 [Github 的文档](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/working-with-forks/syncing-a-fork) 了解如何让 fork 的项目与上游代码同步。

你可以 star/watch 本项目或者 follow 作者来及时获得新功能更新通知。


# 二、本地安装
### PC安装3.10及以上的[python](https://www.python.org/)版本，注意安装步骤里把python添加到系统环境变量（google安装步骤）

<div align="left">
  <img src="https://github.com/Toperlock/sing-box-subscribe/assets/86833913/f387322b-a602-40df-b3b6-95561329f2f8" alt="install" width="60%" />
</div>

### 在终端输入下面指令安装依赖（Mac把pip改为pip3）：

```
pip install -r requirements.txt
```

<div align="left">
  <img src="https://github.com/Toperlock/sing-box-subscribe/assets/86833913/0fc03b49-4c57-4ef3-a4fc-044c1a108d75" alt="install" width="60%" />
</div>

### 下载这个 `sing-box-subscribe` 项目，打开终端进入当前项目路径（可以直接在文件路径输入`cmd`）

<div align="left">
  <img src="https://github.com/Toperlock/sing-box-subscribe/assets/86833913/73f05ba8-105c-4f10-8e6c-16e27f26c084" alt="run" width="60%" />
</div>

### 把订阅链接放到 `providers.json` ，编辑好 `config_template_groups_tun.json` 模板使用下面的命令运行脚本：

```
python main.py
```

或者你可以直接带template_index参数选定模板，0表示第一个模板

```
python main.py --template_index=0
```

windows系统建议将命令添加到批处理程序运行。

使用前先编辑 `providers.json` 文件以及 config_template 目录下的 `.json` 模板文件。

已内置懒人 `config_template_groups_rule_set_tun` 文件，请在模板里修改筛选节点
* 实现 `Openai` 分流
* 实现 `Youtube` 分流
* 实现 `Google` 分流
* 实现 `Github` 分流
* 实现 `Telegram` 分流
* 实现 `Twitter` 分流
* 实现 `Facebook` 分流
* 实现 `Instagram` 分流
* 实现 `Bilibili` 分流
* 实现 `Bahamut` 分流
* 实现 `Spotify` 分流
* 实现 `TikTok` 分流
* 实现 `Netflix` 分流
* 实现 `Disney+` 分流
* 实现 `Apple` 分流
* 实现 `Amazon` 分流
* 实现 `Microsoft` 分流
* 实现 `Game` 分流
* 实现 `Hbo` 分流
* 实现 `Prime Video` 分流

# providers.json文件
在这个文件中添加订阅链接，以及基础设置。
```json
{
    "subscribes":[
        {
            "url": "订阅地址",
            "tag": "机场1", //保持默认，除非你知道这是干什么的
            "enabled": true, //启用
            "emoji": 1, //节点名前添加国家emoji
            "subgroup": "", //命名后生成策略组
            "prefix": "", //节点名前加自定义前缀
            "ex-node-name": "网站|流量|过期", //过滤包含关键词的节点
            "User-Agent":"clashmeta" //自定义获取订阅链接的UA，比如:"v2rayNG","Shadowrocket/1900 CFNetwork/1331.0.7 Darwin/21.4.0"
        },
        {
            "url": "订阅地址",
            "tag": "机场2",
            "enabled": false, //不启用
            "emoji": 0,
            "subgroup": "", //命名后生成策略组
            "prefix": "❤️机场前缀 - ",
            "User-Agent":"clashmeta"
        }
    ],
    "auto_set_outbounds_dns":{
        "proxy": "",
        "direct": ""
    },
    "save_config_path": "./config.json",
    "auto_backup": false,
    "exclude_protocol": "ssr", //排除订阅链接里ssr协议节点
    "config_template": "", //自定义正确的网页json配置模板链接
    "Only-nodes": false //开启时，只输出节点内容(不是完整sing-box配置)
}
```
- `url`：必须。

> 支持机场普通的v2订阅链接（**内容为base64编码**）

> 支持机场clash订阅链接

> 支持机场sing-box订阅链接

> 本地文件路径（**内容为标准URI链接或者clash字段**）
       
      本地文件以 `.txt` 后缀，需要在文件中每行一个添加单节点分享链接，比如 `ss://` 开头（非订阅链接）。

      本地文件以 `.yaml` 后缀，填写正确的 clash proxies 字段。
      
      本地文件需要保存到相同盘符，本地路径格式： `/Desktop/sing-box-subscribe/xx.txt` 或者是与 `main.py` 相同文件夹里相对路径格式： `./xx.txt`。

- `tag`：必须。

> config 模板里填上此处写的tag才能添加此订阅。此处的 `"机场1"` 对应 config 模板中的 `"{机场1}"` 具体使用方法可以查看下方的 config 模板部分。

<details>
      <summary>tag截图参考</summary>
   
<div align="left">
<img src="https://github.com/Toperlock/sing-box-subscribe/assets/86833913/781c5bb7-c5c5-467e-a6ae-05ff44a19973" alt="download" width="65%" />
</div>

</details>
      
- `enabled`：非必需。**将其设置为 false 时，此订阅会被忽略**。

- `emoji`：非必需。**将其设置为 false 或 0 时，节点名称不会添加国旗emoji**。

- `subgroup`: 非必需。给订阅链接命名后生成策略组。

- `prefix`：非必需。设置自定义前缀，前缀会添加到对应节点名称前。如果没有设置，则不添加前缀。

- `pex-node-name`：非必需。过滤关键词节点，多个关键词用 "|" 分割。

- `User-Agent`：非必需。可以自定义UA，比如设置UA为"clash.meta"，或者"sing-box"

<details>
      <summary>prefix效果参考</summary>
      
![Snipaste_2023-05-02_12-53-27](https://user-images.githubusercontent.com/21310130/235582317-6bb3d0a6-916f-445f-999b-f17b3db41eea.png)

</details>

- `auto_set_outbounds_dns`：非必需。
> 包含 `proxy` 和 `direct` 设置项。

> `proxy` 和 `direct` 应该设置为 config 模板文件中存在的 `dns server` 的 `tag`。

> 设置此项后，脚本会自动适配 路由规则 到 dns 规则。

> 将路由规则中 `direct` 出站 的 `dns server` 设置为选项中指定的 `direct` 出站。

> 将路由规则中需要代理的 出站 设置为对应的 `proxy` 出站，脚本会自动创建对应出站的 `dns server`，以 `proxy` 设置项指定的 `dns server` 为模板。
 
- `save_config_path`：必需。设置生成的配置文件路径。
 
- `auto_backup`：非必需。
> 设置为 true 时，脚本会将当前使用的sing-box配置文件更名为 `原文件名称.当前时间.bak` 进行备份，避免生成错误的配置文件后无法挽回。
 
- `exclude_protocol`：非必需。
> 设置不解析的协议，多个使用英文逗号分隔，比如ssr,vmess。

> 使用此设置中的协议的分享链接会被忽略。

> sing-box release中的程序没有支持ssr（需要自己添加参数构建），所以此设置可能有用。

- `config_template`：非必需。输入一个正确的网页json配置模板链接，以此模板生成sing-box配置。

- `Only-nodes`：非必需。
> 将其设置为 true 或 1 时，只输出订阅链接 sing-box 格式的节点信息

# config模板文件
脚本会在 config_template 目录下查找 json 模板文件，脚本运行时可以选择使用的模板文件。

比如目录下存在 `tun.json` 和 `socks.json` 两个模板文件。

![Snipaste_2023-03-24_22-16-49](https://user-images.githubusercontent.com/21310130/227548643-ffbf3825-9304-4df7-9b65-82a935227aef.png)

脚本不会检查模板文件的正确性，模板文件不正确会出现错误并无法运行脚本。目录下自带有模板，根据需要修改。

模板文件基本等同于 sing-box config，不过有一些新的参数，比如 `{all}`、`{机场tag}`、`filter`，所有参数仅在 `clash_mode` 的出站方式下才会生效，出站类型为 `urltest`、`selector`。
```json
{
  "tag":"proxy",
  "type":"selector",
  "outbounds":[
    "auto",
    "{all}"//所有订阅所有节点添加到此标记所在位置
  ],
  "filter":[
    //此条过滤将会删除 机场1 中包含 ˣ² 的节点
    {"action":"exclude","keywords":["ˣ²"],"for":["机场1"]}
  ]
},
{
  "tag":"netflix",
  "type":"selector",
  "outbounds":[
    "{机场1}",//订阅tag为 机场1 的节点将添加到此标记所在位置
    "{机场2}"//订阅tag为 机场2 的节点将添加到此标记所在位置
  ],
  "filter":[
    //如果机场1，机场2有节点 sg、新加坡、tw、台湾，他们共同组成 netflix 组
    {"action":"include","keywords":["sg|新加坡|tw|台湾"]},
    //for里面设置为机场1，代表此条规则只对机场1起作用
    {"action":"exclude","keywords":["ˣ²"],"for":["机场1"]}
    //执行完第二个规则后 netflix 组将机场1 中包含 ˣ² 的节点删掉
  ]
}
```
- `{all}`：表示所有订阅中的所有节点。脚本会将所有节点添加到有此标识的 `outbounds` 中。

- `{机场tag}`：在 `providers.json` 中设置的机场 `tag` 可以用于此处，代表此订阅中的所有节点。

- `filter`：非必需。节点过滤，为一个数组对象，可以添加任意条规则，格式为:
```json
"filter":[
    {"action":"include","keywords":["保留关键字1|保留关键字2"]},
    {"action":"exclude","keywords":["排除关键字1|排除关键字2"],"for":["机场1tag","机场2tag"]}
  ]
```
- **关键字大小写敏感**

- `include`：后面添加要保留的关键字，用 '|' 连接多个关键字，名称中包含这些关键字的节点都将被保留，其他节点会被删除。

- `exclude`：后面添加要排除的关键字，用 '|' 连接多个关键字，名称中包含这些关键字的节点都将被删除，其他节点会被保留。

- `for`：非必需。设置机场 `tag`，可以多个，表示此规则只对指定的机场起作用，其他机场会忽略这个规则。

多个规则会按顺序执行过滤。

# Windows sing-box 使用方法

1. 下载Windows客户端程序[sing-box-windows-amd64.zip](https://github.com/SagerNet/sing-box/releases)。
2. 新建一个 `.bat` 批处理文件，内容为 `start /min sing-box.exe run`。
3. 参考[客户端配置](https://github.com/chika0801/sing-box-examples/blob/main/Tun/config_client_windows.json)示例，按需修改后将文件名改为 **config.json**，与 **sing-box.exe**，批处理文件放在同一文件夹里。
4. 右键点击 **sing-box.exe** 选择属性，选择兼容性，选择以管理员身份运行此程序，确定。
5. 运行批处理文件，在弹出的用户账户控制对话框中，选择是。

## 隐藏Windows运行sing-box弹出的cmd窗口

> 使用WinSW把sing-box.exe设置成Windows服务，[WinSW教程](https://www.jianshu.com/p/fc9e4ea61e13)

> XML配置文件修改
```xml
<service>
  <id>sing-box</id>
  <name>sing-box</name>
  <description>sing-box Service</description>
  <executable>./sing-box.exe</executable>
  <log mode="reset"></log>
  <arguments>run</arguments>
</service>
```
<details>
      <summary>Windows sing-box 文件夹内容</summary>
 
<div align="left">
  <img src="https://github.com/Toperlock/sing-box-subscribe/assets/86833913/c6a815bf-b542-43c6-aeb6-84020586a1f1" alt="download" width="50%" />
</div>

</details>

## 在非图形化客户端，不使用tun的话的操作

比如在windows上用内核跑 sing-box，在入站inbounds里删掉tun字段：

```json
"inbounds": [
    {
      "type": "mixed",
      "listen": "127.0.0.1",
      "listen_port": 2080, //此端口要和windows代理端口一致
      "sniff": true,
      "set_system_proxy": true,
      "sniff_override_destination": false,
      "domain_strategy": "ipv4_only"
    }
  ]
```

<div align="left">
  <img src="https://github.com/Toperlock/sing-box-subscribe/assets/86833913/387f2077-b8b6-42ed-9658-361b28179db2" alt="download" width="50%" />
</div>

<details>
      <summary><b>效果参考</b></summary>

具体效果根据个人的出站及规则设置决定。

<div align="left">
  <img src="https://user-images.githubusercontent.com/21310130/227577941-01c80cfc-1cd9-4f95-a709-f5442a2a2058.png" alt="download" width="50%" />
  <img src="https://user-images.githubusercontent.com/21310130/227577968-6747c7aa-db61-4f6c-b7cc-e3802e34cc3d.png" alt="download" width="50%" />
  <img src="https://github.com/Toperlock/sing-box-subscribe/assets/86833913/955968d7-98e7-4bd2-a582-02576877dba1" alt="download" width="50%" />
  <img src="https://github.com/Toperlock/sing-box-subscribe/assets/86833913/9e7c35ff-c6c4-46c4-a74b-624ff72c17ea" alt="download" width="50%" />
</div>

</details>

## Star 历史

[![Star History Chart](https://api.star-history.com/svg?repos=Toperlock/sing-box-subscribe&type=Date)](https://star-history.com/#Toperlock/sing-box-subscribe&Date)

# 感谢
- [一佬](https://github.com/xream)
- [sing-box](https://github.com/SagerNet/sing-box)
- [yacd](https://github.com/haishanh/yacd)
- [clash](https://github.com/Dreamacro/clash)
- [sing-box-examples@chika0801](https://github.com/chika0801/sing-box-examples)

部分协议解析参考了[convert2clash](https://github.com/waited33/convert2clash)

部分clash2v2ray参考了[clash2base64](https://github.com/yuanyiwei/toys/blob/master/DEPRECATED/clash/clash2base64.py)

同步代码参考了[ChatGPT-Next-Web](https://github.com/Yidadaa/ChatGPT-Next-Web)

感谢@SayRad的越南翻译
