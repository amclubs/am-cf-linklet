# [am-cf-linklet](https://github.com/amclubs/am-cf-linklet)

#
▶️ **新人[YouTube](https://youtube.com/@am_clubs?sub_confirmation=1)** 需要您的支持，请务必帮我**点赞**、**关注**、**打开小铃铛**，***十分感谢！！！*** ✅
</br>🎁请 **follow** 我的[GitHub](https://github.com/amclubs)、给我所有项目一个 **Star** 星星（拜托了）！你的支持是我不断前进的动力！ 💖
</br>✅**解锁更多技能** [加入TG群【am_clubs】](https://t.me/am_clubs)、[YouTube频道【@am_clubs】](https://youtube.com/@am_clubs?sub_confirmation=1)、[【博客(国内)】](https://amclubss.com)、[【博客(国际)】](https://amclubs.blogspot.com) 
</br>✅点击观看教程[CLoudflare免费节点](https://www.youtube.com/playlist?list=PLGVQi7TjHKXbrY0Pk8gm3T7m8MZ-InquF) | [VPS搭建节点](https://www.youtube.com/playlist?list=PLGVQi7TjHKXaVlrHP9Du61CaEThYCQaiY) | [获取免费域名](https://www.youtube.com/playlist?list=PLGVQi7TjHKXZGODTvB8DEervrmHANQ1AR) | [免费VPN](https://www.youtube.com/playlist?list=PLGVQi7TjHKXY7V2JF-ShRSVwGANlZULdk) | [IPTV源](https://www.youtube.com/playlist?list=PLGVQi7TjHKXbkozDYVsDRJhbnNaEOC76w) | [Mac和Win工具](https://www.youtube.com/playlist?list=PLGVQi7TjHKXYBWu65yP8E08HxAu9LbCWm) | [AI分享](https://www.youtube.com/playlist?list=PLGVQi7TjHKXaodkM-mS-2Nwggwc5wRjqY)

## 介绍

一个使用 Cloudflare Pages 创建的 URL 缩短器

*演示站点* :  [linklet.amcloud.filegear-sg.me](https://linklet.amcloud.filegear-sg.me)

### 1.利用 Cloudflare Pages 部署

1. Fork [linklet 仓库](https://github.com/amclubs/am-cf-linklet.git)。
2. 登录到 [Cloudflare](https://dash.cloudflare.com) 控制台。
3. 在 Cloudflare 控制台，选择 <kbd>Workers & Pages</kbd> > <kbd>Create application</kbd> > <kbd>Pages</kbd> > <kbd>Connect to Git</kbd>。
4. 选择 Fork 的仓库，若没有该仓库，请点击 [Cloudflare Pages 链接](https://github.com/settings/installations/46795069)配置 Cloudflare 访问个人的 GitHub 仓库权限。
5. 选中 Fork 的仓库，点击<kbd>Begin setup</kbd>完成部署。
6. 在 Cloudflare 控制台创建 D1 数据库，依次点击 <kbd>Workers & Pages</kbd> > <kbd>D1</kbd> > <kbd>Create database</kbd> > <kbd>Dashboard</kbd>，输入 Database name 点击 <kbd>Create</kbd> 完成数据库的创建。
7. 点击 <kbd>Console</kbd>，输入以下 SQL 命令创建表：

```sql
DROP TABLE IF EXISTS links;
CREATE TABLE IF NOT EXISTS links (
  `id` integer PRIMARY KEY NOT NULL,
  `url` text,
  `slug` text,
  `ua` text,
  `ip` text,
  `status` int,
  `create_time` DATE
);
DROP TABLE IF EXISTS logs;
CREATE TABLE IF NOT EXISTS logs (
  `id` integer PRIMARY KEY NOT NULL,
  `url` text ,
  `slug` text,
  `referer` text,
  `ua` text ,
  `ip` text ,
  `create_time` DATE
);
```

8. 选择部署完成的 linklet 项目，在 Cloudflare 控制台依次点击<kbd>Settings</kbd> > <kbd>Functions</kbd> > <kbd>Add bindings</kbd>，输入 Variable name 值 **DB** 并选择 D1 Database **linklet**，点击 <kbd>Save</kbd> 保存，设置如下表：

    | Variable name | D1 database |
    | :------------ | :---------- |
    | DB            | linklet     |

9. 为了生效 D1 数据库配置，需完成项目的重新部署。

### 2.API 方式生成短网址

请求：

```http
### 生成随机短链接
POST https://linklet.amcloud.filegear-sg.me/create
Content-Type: application/json

{
  "url": "https://am.809098.xyz/2024/07/18/am-trojan-up/"
}

### 生成指定 slug 短链接
POST https://linklet.amcloud.filegear-sg.me/create
Content-Type: application/json

{
  "url": "https://am.809098.xyz/2024/07/18/am-trojan-up/",
  "slug": "llama"
}

```

响应：

```json
{
  "slug": "<slug>",
  "link": "https://am.809098.xyz/abc<slug>"
}
```
  
# 
<center>
<details><summary><strong> [点击展开] 赞赏支持 ~🧧</strong></summary>
*我非常感谢您的赞赏和支持，它们将极大地激励我继续创新，持续产生有价值的工作。*

- **USDT-TRC20:** `TWTxUyay6QJN3K4fs4kvJTT8Zfa2mWTwDD`
- **TRX-TRC20:** `TWTxUyay6QJN3K4fs4kvJTT8Zfa2mWTwDD`

<div align="center"> 
  <img src="https://github.com/user-attachments/assets/e6cdc42a-6374-4722-b833-601738f72196" width="200"></br> 
  TRC10/TRC20扫码支付 
</div> 
</details>
</center>

 #
 免责声明:
 - 1、该项目设计和开发仅供学习、研究和安全测试目的。请于下载后 24 小时内删除, 不得用作任何商业用途, 文字、数据及图片均有所属版权, 如转载须注明来源。
 - 2、使用本程序必循遵守部署服务器所在地区的法律、所在国家和用户所在国家的法律法规。对任何人或团体使用该项目时产生的任何后果由使用者承担。
 - 3、作者不对使用该项目可能引起的任何直接或间接损害负责。作者保留随时更新免责声明的权利，且不另行通知。
 
