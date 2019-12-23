---
published: true
title: (Hugo-開發-02) --- Hugo 環境建立
layout: post
author: Allen
category: Hugo
tags: 
  - Hugo
  - 前端
  - 教學
comments: true
---

![logo](/images/blog/20191216/20191216-000.png)

# 安裝
以 Windows 為例，可以下載
![hugo](/images/blog/20191216/20191216-001.png)

透過 https://github.com/gohugoio/hugo/releases
下載

# 設定 Windows 環境變數
![hugo](/images/blog/20191216/20191216-002.png)

將下載下來的 *hugo.exe* 增加到 Windows 的 *PATH* 環境變數設定

# 建立新網站目錄

我們使用 force 指令
![hugo](/images/blog/20191216/20191216-003.png)

同時搭配 Github 進行程式碼管理
![hugo](/images/blog/20191216/20191216-004.png)

# 下載 Theme
https://github.com/budparr/gohugo-theme-ananke

![hugo](/images/blog/20191216/20191216-007.png)

下載後放在 Theme 目錄中並改名為 ananke 目錄
![hugo](/images/blog/20191216/20191216-008.png)

修改 *config.toml* 檔案，增加 *theme = "ananke"*
完整檔案如下
```toml
baseURL = "http://example.org/"
languageCode = "en-us"
title = "My New Hugo Site"
theme = "ananke"
```

# 建立第一篇文章

![hugo](/images/blog/20191216/20191216-005.png)

修改內容
```markdown
---
title: "First"
date: 2019-12-14T16:57:38+08:00
draft: false
---

Hellow World!!
```

# 測試結果
![hugo](/images/blog/20191216/20191216-006.png)

開啟瀏覽器 http://localhost:1313/
![hugo](/images/blog/20191216/20191216-009.png)