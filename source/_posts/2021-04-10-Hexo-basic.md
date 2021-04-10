---
title: Hexo 基本操作
comment: true
date: 2021-04-10 15:02:25
categories:
tags: [hexo]
---
# 安裝

```bash
$ hexo init [folder]
```

如果沒有指定，會在目前資料夾建立網站
<!--more-->
# 新增文章

```jsx
hexo new <postName>
```

# 產生靜態檔案

會產生 public 目錄，如果執行 `hexo deploy` 部署，就會將這個目錄底下的內容上傳。

```bash
$ hexo generate
或
$ hexo g
```

# 啟動本機伺服器

```bash
$ hexo server
或
$ hexo s
```

# 部署網站

```bash
$ hexo deploy
或
$ hexo d
```

清除快取檔案(db.json)，並刪除已產生的靜態檔案(public)

如果發現任何修改都不生效，可以執行這個指令。

```bash
$ hexo clean
```

# 🌎  Resources

- 參考網址：[https://wst24365888.github.io/hexo-site/](https://wst24365888.github.io/hexo-site/)
- 官方指令：[https://hexo.io/zh-tw/docs/commands.html#init](https://hexo.io/zh-tw/docs/commands.html#init)
- 寫作：[https://hexo.io/zh-tw/docs/tag-plugins](https://hexo.io/zh-tw/docs/tag-plugins)