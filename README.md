# [am-cf-linklet](https://github.com/ansoncloud8/am-cf-linklet)
▶️ **新人[YouTube](https://youtube.com/@AM_CLUB)** 需要您的支持，请务必帮我**点赞**、**关注**、**打开小铃铛**，***十分感谢！！！*** ✅
</br>🎁 不要只是下载或Fork。请 **follow** 我的GitHub、给我所有项目一个 **Star** 星星（拜托了）！你的支持是我不断前进的动力！ 💖
</br>✅**解锁更多技术请访问[【个人博客】](https://am.809098.xyz)**,加入TG群[【AM科技 | 分享交流群】](https://t.me/AM_CLUBS) 
#

# 免责声明

### 用途
该项目被设计和开发仅供学习、研究和安全测试目的。它旨在为安全研究者、学术界人士和技术爱好者提供一个了解和实践网络通信技术的工具。

### 合法性
使用者在下载和使用该项目时，必须遵守当地法律和规定。使用者有责任确保他们的行为符合其所在地区的法律、规章以及其他适用的规定。

### 免责
1. 作为该项目的作者，我（以下简称“作者”）强调该项目应仅用于合法、道德和教育目的。
2. 作者不鼓励、不支持也不促进任何形式的非法使用该项目。如果发现该项目被用于非法或不道德的活动，作者将强烈谴责这种行为。
3. 作者对任何人或团体使用该项目进行的任何非法活动不承担责任。使用者使用该项目时产生的任何后果由使用者本人承担。
4. 作者不对使用该项目可能引起的任何直接或间接损害负责。
5. 通过使用该项目，使用者表示理解并同意本免责声明的所有条款。如果使用者不同意这些条款，应立即停止使用该项目。

作者保留随时更新本免责声明的权利，且不另行通知。最新的免责声明版本将会在该项目的 GitHub 页面上发布。

## 介绍

一个使用 Cloudflare Pages 创建的 URL 缩短器

*演示站点* :  [linklet.amcloud.filegear-sg.me](https://linklet.amcloud.filegear-sg.me)

### 1.利用 Cloudflare Pages 部署

1. Fork [linklet 仓库](https://github.com/ansoncloud8/am-cf-linklet.git)。
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
<center><details><summary><strong> [点击展开] 赞赏支持 ~🧧</strong></summary>
*我非常感谢您的赞赏和支持，它们将极大地激励我继续创新，持续产生有价值的工作。*
  
- **USDT-TRC20:** `TWTxUyay6QJN3K4fs4kvJTT8Zfa2mWTwDD`
  
</details></center>




