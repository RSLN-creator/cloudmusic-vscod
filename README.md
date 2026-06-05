<h1 align="center">
  <img src="https://s3.ax1x.com/2021/03/07/6M7aLj.png" alt="CLOUDMUSIC"></img>
  <br></br>
  🎶 CLOUDMUSIC
  <br></br>
</h1>

<div align="center">

> Netease Music for VS Code

[![Marketplace](https://img.shields.io/visual-studio-marketplace/v/yxl.cloudmusic.svg?label=Marketplace&style=for-the-badge&logo=visual-studio-code)](https://marketplace.visualstudio.com/items?itemName=yxl.cloudmusic)
[![Installs](https://img.shields.io/visual-studio-marketplace/i/yxl.cloudmusic.svg?style=for-the-badge)](https://marketplace.visualstudio.com/items?itemName=yxl.cloudmusic)
[![Rating](https://img.shields.io/visual-studio-marketplace/stars/yxl.cloudmusic.svg?style=for-the-badge)](https://marketplace.visualstudio.com/items?itemName=yxl.cloudmusic)

简体中文 | [English](./README.EN.md)

</div>

## 本仓库修改说明

本仓库基于 [yxl76/cloudmusic-vscode](https://github.com/yxl76/cloudmusic-vscode) 修改，主要解决网易云音乐新风控导致的登录失败问题。

### 修改内容

1. **登录 API 从 weapi 迁移到 eapi**：原有登录接口使用 `weapi` 加密方式，容易被网易云新风控拦截。已将所有登录相关接口迁移到 `eapi` 加密方式，降低被风控的概率。

2. **API 域名更新**：将 `interface3.music.163.com` 统一替换为 `interface.music.163.com`，适配网易云最新的 API 域名。

3. **新增 Cookie Login 登录方式**：在原有邮箱、手机、验证码、二维码登录方式之外，新增 Cookie 登录方式。用户可以在浏览器中登录网易云音乐后，将 `MUSIC_U` Cookie 值手动导入插件，完全绕过 API 风控。

4. **appver 更新**：将客户端版本号从旧版更新为 `9.2.30`，模拟最新客户端请求。

### Cookie Login 使用方法

1. 在浏览器中访问 [music.163.com](https://music.163.com) 并登录
2. 打开浏览器开发者工具（F12）→ Application → Cookies
3. 找到 `music.163.com` 域名下的 `MUSIC_U` Cookie，复制其值
4. 在 VS Code 中打开命令面板（Ctrl+Shift+P），搜索 "CloudMusic: Sign in"
5. 选择 "Cookie" 登录方式，粘贴 `MUSIC_U` 的值即可

### 安装修改版插件

从 [GitHub Releases](https://github.com/RSLN-creator/cloudmusic-vscod/releases) 下载对应平台的 `.vsix` 文件，然后：

```bash
code --install-extension cloudmusic-9.22.0.vsix
```

或者手动替换：下载 Release 中的 `dist` 压缩包，解压覆盖到 VS Code 扩展目录下的 `dist` 文件夹即可。

---

## Table of contents

- [Table of contents](#table-of-contents)
- [Features](#features)
- [Requirements](#requirements)
- [Usage](#usage)
- [Contributions](#contributions)
- [Release Notes](#release-notes)
- [API](#api)
- [Acknowledgements](#acknowledgements)

## Features

- 简单：开箱即用，无需安装、修改任何文件
- 快速：使用本机模块，资源占用低，速度快
- 强大：借助网页 API，能实现所有常用功能

已实现的功能：

- 每日签到
- 歌曲播放，收藏，喜欢
- 听歌打卡
- 心动模式
- 私人 FM
- 评论（单曲/歌单...）
- 歌词显示
- ~~解锁变灰音乐~~
- 搜索（热搜/单曲/专辑/歌手...）
- 排行榜（音乐榜/歌手榜...）
- 发现（新歌速递/新碟上架...）
- 播单/节目
- 本地曲库
- 缓存管理
- 可选无损音质
- 媒体控制支持
- 更多功能等待发现

扩展产生的所有本地内容都位于`$HOME/.cloudmusic`文件夹中

## Requirements

## Usage

![Usage](https://z3.ax1x.com/2021/07/31/WjLd61.png)

支持海外用户，可以在设置中开启（`cloudmusic.network.foreignUser`）

## Contributions

完整列表请查看`Feature Contributions`

## Release Notes

[CHANGELOG](./CHANGELOG.md)

## API

[API](./doc/API.md)

## Acknowledgements

受到以下项目的启发：

- [swdc-vscode-musictime](https://github.com/swdotcom/swdc-vscode-musictime)
- [vsc-netease-music](https://github.com/nondanee/vsc-netease-music)
- [netease-music-tui](https://github.com/betta-cyber/netease-music-tui)

感谢这些超棒的项目：

- [NeteaseCloudMusicApi](https://github.com/Binaryify/NeteaseCloudMusicApi)
- [neon](https://github.com/neon-bindings/neon)
- [rodio](https://github.com/RustAudio/rodio)
- [UnblockNeteaseMusic](https://github.com/nondanee/UnblockNeteaseMusic)
