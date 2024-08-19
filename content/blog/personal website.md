---
title: "How to Build a FREE Personal Website IN 1 HOUR?"
date: "2024-08-19T00:19:48+08:00"
tags: ["Personal Website", "Tutorial"]
draft: false
---
如何在一小時內建立你的個人網頁？而且還免費！？

---

## 前言
最近我在學習各種知識時整理了很多東西，隨後想到可以分享到網路上跟大家交流討論，所以就開始了我的個人網站開發之旅啦！

其實，我之前就嘗試過要架設個人網站，但遇到不少阻礙。簡言之，好用的要錢，但免費的又有以下問題：
* 找不到喜歡的主題
* 現成主題有點醜，想手動修改template卻得要修改大量的HTML和CSS
* 繁瑣的部署及維護程序

在網路上搜尋一陣子後，看到Hugo的PaperMod Theme簡潔的版面及資料夾結構，加上GitHub上有**9.4K**顆星星，就決定試看看它了，沒想到真的解決了以上痛點，而且操作上非常容易！

---
## 我參考了哪些資料？
你可以看參考資料自行完成個人網站的架設，也可以直接使用我提供的簡化版文字教學來快速完成。

我首先看了[這個YouTube影片](https://www.youtube.com/watch?v=hjD9jTi_DQ4&list=PLeiDFxcsdhUrzkK5Jg9IZyiTsIMvXxKZP&index=1&t=2s)，約1小時長，這位老兄講得很簡單，手把手帶你如何使用hugo的papermod theme建立基礎的個人網站，跟著做完之後，會對Hugo開發有基礎的認知，網站雛形也出來了。

由於上述影片中沒有提到進階功能怎麼設定，所以我接著參考[PaperMod的GitHub](https://github.com/adityatelange/hugo-PaperMod)，裡面有default模板可供參考。

## 作法
進入正題，我將詳細介紹如何完成網站架設。

以下參考[PaperMod的安裝步驟](https://github.com/adityatelange/hugo-PaperMod/wiki/Installation#getting-started-)（以MacOS為例，其他作業系統請參考官方文件），可以直接看下面的教學，跑不動再去找解答。
### Step 1: 安裝Homebrew和Hugo
**Homebrew**是一個在MacOS中非常好用的套件管理工具，透過它可以輕鬆安裝、更新和管理各種軟體包和工具。

**Hugo**是一個基於go的疾速架站框架，非常容易使用，且提供很多主題，不需要碰到source code也能輕鬆完成個人網站的開發與部署。
```bash
# 打開 Terminal，安裝 Homebrew，並確認已安裝完成
$ /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
$ brew -v # 將顯示Homebrew版本 (Homebrew 4.3.16)

# 使用 Homebrew安裝 Hugo，並確認已安裝完成
$ brew install hugo
$ hugo version # 將顯示 Hugo版本 (hugo v0.133.0...)
```

### Step 2: 使用PaperMod建立網頁模版
```PaperMod```的版面非常地簡潔乾淨，具備個人網站必備的Profile, Home, Search Template, Archive等功能。
創建貼文也相當容易，只要新增資料夾和markdown(.md)檔案即可。常見功能如新增圖片、連結等都能非常方便地處理完成。
甚至支援Google Analytics, SEO等進階功能。(我還沒研究這部分，目前只是想先架個workable的網站)

我覺得[這個利用PaperMod開發的個人網站](https://arkalim.netlify.app/)做得還不錯，可供參考。

```bash
# 建立你的網站並進入該資料夾中
$ hugo new site yourWebsiteName --format yaml # 把yourWebsiteName改成你想要的網站名稱
$ cd yourWebsiteName # 把yourWebsiteName改成你想要的網站名稱

# 建立git
$ git init

# 使用git submodule加載PaperMod主題
$ git submodule add --depth=1 https://github.com/adityatelange/hugo-PaperMod.git themes/PaperMod
$ git submodule update --init --recursive

# 讓submodule維持在最新版本，同時確保本地的更改不會被覆蓋
$ git submodule update --remote --merge

# 讓PaperMod成為你的網站主題
$ echo "theme: PaperMod" >> hugo.yaml

# 讓網頁跑起來
$ hugo server
...
Built in 49 ms
Environment: "development"
Serving pages from disk
Web Server is available at //localhost:1313/ (bind address 127.0.0.1) 
```
這樣就完成初版網頁了，你可以到瀏覽器上輸入```localhost:1313```看看網頁的樣子。

---

## 客製化網頁
接下來就是客製化了，建議你先複製我GitHub上的[hugo.yaml](https://github.com/karta1502545/Chun-Yi-Lee)，再根據以下教學修改參數。如果你跟著教學做遇到問題，可以直接參考我的[GitHub](https://github.com/karta1502545)中```content```及```hugo.yaml```的設定。

基本上你需要做這幾件事：
### 決定右上角的menu有哪些頁面
```yaml
menu:
  main:
    - identifier: archive
      name: Archive
      url: /archive/
      weight: 10
    - identifier: blog
      name: Blog
      url: /blog/
      weight: 20
    - identifier: projects
      name: Projects
      url: /projects/
      weight: 30
    - identifier: experiences
      name: Experiences
      url: /experiences/
      weight: 40
    - identifier: search
      name: Search
      url: /search/
      weight: 50
    - identifier: CV
      name: CV
      url: yourCVURL
      weight: 60
```
我的個人網頁設定是這樣，weight越大會被擺到越右邊。

### 設定初始頁面的頭貼和簡介

這邊要在```static```裡面放一張照片，並在```hugo.yaml```上寫上圖片位置。
我是在```static```底下創個```img```資料夾，然後把頭貼放在裡面。
```yaml
params:
  ...
  # profile-mode
  profileMode:
    enabled: true # needs to be explicitly set
    title: Chun-Yi Lee
    subtitle: "A curious software engineer who explores all kinds of tech and loves making it easy for others to understand."
    imageUrl: "img/headPhoto.jpg"
    imageWidth: 240
    imageHeight: 260
    imageTitle: Chun-Yi's handsome headshot
    buttons:
      - name: Blog
        url: blog
      - name: Tags
        url: tags
```
### 在Blog資料夾底下創建貼文

你只需要在```content```底下建立```blog```資料夾，並在底下新增一個```firstPost.md```，把以下模板貼上去，就完成了。

結構如下：
```
content/
└── blog/
    └── firstPost.md
```

```markdown
---
title: "VideoToText"
date: "2024-08-18T23:59:48+08:00"
draft: false
---

## This is my first post!
Hello welcome to my first post!
```
experiences, projects的建構同以上流程。

### 設置Archive頁面
```Archive```頁面可以讓使用者根據時間線查看你的貼文。
你只需要在```content```底下新增一個```archive.md```，把以下模板貼上去，就完成了。
```markdown
---
title: "Archive"
layout: "archive"
url: "/archive/"
summary: archive
---
```

### 設置Search頁面
```Search```頁面可以讓使用者用各種語言查詢你的貼文標題及內容。
你只需要在```content```底下新增一個```search.md```，把以下模板貼上去，並且在```hugo.yaml```新增幾行程式碼，就完成了。
```markdown
---
title: "Search" # in any language you want
layout: "search" # necessary for search
url: "/search/"
# description: "Description for Search"
summary: "search"
placeholder: "type in your keywords.."
---
```

```yaml
# (in the end of hugo.yaml, add these lines)
outputs:
  home:
    - HTML
    - RSS
    - JSON # necessary for search
```

---

## 部署網站
現在要把剛剛開發好的個人網站publish到Internet上。
這邊不多贅述，請參考[此教學影片](https://youtu.be/hjD9jTi_DQ4?list=PLeiDFxcsdhUrzkK5Jg9IZyiTsIMvXxKZP&t=2230)，部署流程大約十分鐘。

## 你還可以做的事
1. 新增按讚、評論欄位
2. 了解如何在貼文上嵌入照片、YouTube影片
3. 研究PaperMod的Document挖掘更多好用的功能

---

非常感謝你看到這邊，如果這篇文章對你有用，請分享給你的朋友，謝謝！
