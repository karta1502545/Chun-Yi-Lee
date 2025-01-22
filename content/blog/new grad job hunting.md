---
title: "2025美國CS New Grad上岸心得"
date: "2025-01-19T15:00:00-05:00"
# tags: []
draft: false
---

## 特別感謝
學長姐與幫我內推的好心前輩們

香檳刷題群所舉辦的活動，包含遇到楷訓學長以及王超學長的演講

UIUC同屆同學的相互分享與支持

室友兼高中同學幫我mock interview以及維護良好的面試環境

家人與女友（偷偷工商[女友的medium](https://medium.com/@annyf)）的支持，特別是女友在暑假幫我練習英文口說、BQ，還有找工時無數次精神上的支持與鼓勵<3

---

嗨，我是俊逸，最近剛從UIUC畢業，正準備要到加州工作了。趁記憶猶新，紀錄在學校的最後一學期的掙扎與奮鬥，也給之後想到美國找軟體工作的同學一個參考。

鑑於網路上已經有很多厲害的前輩分享心得，本文僅包含個人找工的統計數據，以及自認有用的概念與資源，盡可能減少閱讀負擔。

**本篇文章適合給沒有正職經驗，想要到美國讀碩找軟體工作，或正在找的同學，希望可以幫助到你們。**

對於找工的任何面向有問題，或單純想聊聊的話，都歡迎聯絡我的[LinkedIn](https://www.linkedin.com/in/cy-lee-1502545)或[Facebook](https://www.facebook.com/profile.php?id=100004892852040)！

## 我的履歷
- 清大資工22級 -> UIUC MCS
- 新創前後端實習4個月 + 聯發科暑期實習2個月

## 找工作統計數據
*2024.07 - 2024.12*
### 投履歷數量 
（收到回覆數量/投遞數量）
- 大公司官網: 4/300
- 內推: 3/20 (非常感謝幫我內推的所有學長姐與前輩)
- GitHub: 10/500 (量多但多數OA止步)
- 其他（如LinkedIn, HandShake）: 4/2300(多數由自動投履歷程式貢獻)

### 面試數量  
**美國**
```
- Online Assessment: 15
    - Codeium, OKX, Stripe, Uber*2, BCG X, Morgan Stanley(沒做), HeyGen(沒做)
    - 白嫖: IBM, Cisco, ZipRecruiter
- Interview: 9 + 2(from OA)
    - 一面: Talroo, CV小公司
    - 二面: Apple, TikTok DevOps, WeRide(沒面), Crypto小公司
    - Final Round: **Tesla**(3輪7面), TikTok SRE(3輪3面), Pony AI(2輪5面)
    - **Offer**: **Meta**(OA+1輪3面), iOT小公司(3輪3面)
```

**台灣**
```
- Online Assessment: 4
    - Amazon SDE, NVidia firmware, Circle
- Interview: 6
    - 一面: TSMC IT, Yahoo Backend
    - Final Round: **Google**(2輪4面, Team Match中), Qualcomm(2輪2面), Nokia(3輪3面)
    - **Offer**: Dell
```

## 主題  
[了解遊戲規則](#了解遊戲規則)  
[找工作時程分配](#找工作時程分配)  
[Day1原則](#day1原則)  
[投履歷](#投履歷)  
[面試](#面試)  
[其他](#其他)  
[FAQ](#faq)  
[前輩分享](#前輩分享)  
[參考資源](#參考資源)  

### 了解遊戲規則
看[王超學長的頻道](https://www.youtube.com/watch?v=E51Zdc2ctrA)關於如何在美國拿到面試的影片（在此特別感謝楷訓學長邀請王超學長到源來適你演講，擬定戰略時幫助很大）

### 找工作時程分配
找工作好比打遊戲，要一層一層破關，前面關卡破了再去破後面的關卡。

參照找工流程（修/投履歷 -> OA -> 面試）來說，OA或面試數量不夠的話，先把時間優先花在投和優化履歷。若收到OA了，則多花些時間在刷題、找考古。也就是說，在還沒有面試或OA時，應該花最多時間在投履歷，而非其他事情上。

此外，找工作很花時間，我個人是把找工作當成全職工作在做。為了騰出時間全職找工作，我做了以下事情：修涼課、少做專案、多找內推、每天刷各大公司官網、有空就和同學或[和ChatGPT做mock interview](https://www.youtube.com/watch?v=gkRvfvwy83g)。

### Day1原則
- 看到職缺就第一時間投遞
- 有些平台更新得比其他平台更快，需多方比較，搶快
- 收到OA儘早研究考古並寫完，不要拖到最後一天，公司收滿一定數量的人就不會再收新的人了

### 投履歷
```
- 投履歷很煩但卻是最重要的一步
    - 多投履歷 -> 更多面試 -> 熟悉面試 -> 拿到offer
- 大公司先投（8成面試來自大公司，但大公司投履歷時間佔比僅2-3成）
    - 把各大公司career page加入書籤，每天刷，有新的就投
    - 小公司填寫履歷格式雜亂，要花很多時間投遞，拿到面試的機率低，成效差
- 能內推就內推
- Day1投履歷（一開缺就投）
- 找星星數不要太高，但更新及時的GitHub page（Google搜尋：2025 new grad swe github）
- 自動化填履歷表格
    - Simplify: https://simplify.jobs/
    - LinkedIn自動投履歷程式: https://github.com/feder-cr/Jobs_Applier_AI_Agent
```

### 面試
- BQ準備方式，請參照徹底擊碎行為面試，每個BQ問題都有至少一個故事對應（約10個）
- 了解並熟悉不同考核方向與不同題型的考核重點與評分機制（問hr和找一畝）
- 多看幾遍JD和公司產品
- 要熟悉履歷上的經歷，並應用在BQ當中。履歷上的經歷與BQ問題之間，要建立像關聯性資料庫多對多的概念。如此一來，面試官不管從BQ問或從經歷問，都能應答如流。
- 言談中展現對自己能力的自信，與該職位的了解與熱情
- 以戰養戰，反省並針對弱點改進

### 其他
```
- 針對弱點加強
    - 題刷不夠 沒看考古
        - 多刷題多看考古
    - BQ故事不熟 講題不清楚 英文不流利
        - 找同學模擬面試，找ChatGPT練習BQ
        - 不要害羞，也不用怕自己講不好（講不好才需要練！）
- 建群互相分享找工資訊
    - 主動和同學交流各公司開缺、面試資訊，以及找mock interview的夥伴大量練習，打團戰很重要
    - 問你身邊面試比較多的同學怎麼做的，向大師學習
- 健康第一
    - 累了的話，轉移注意力，好好休息再出發，減少內耗與自我批判
- 保持信念
    - 每天收拒信代表投得足夠多，面試被拒代表多練習一次interview
    - 收到拒信時我就去投履歷，維持pending狀態的申請數量
```

## FAQ
**1. 刷題要刷多少才夠？**

我在LeetCode上大約400題，但題數因人而異。首先至少挑一個選單去刷（Neetcode 150, Grind 169），刷完之後加強陌生主題。收到特定公司面試時，根據考古再去多刷相關題目。

如果某一題寫起來卡卡的，直接找YouTube影片講解，理解後再重新寫一遍，會是最有效率的做法。請看參考資源的推薦頻道。

**2. 履歷修到什麼程度才夠？**

在找工作的一開始先產生一版履歷，之後一邊投一邊修，履歷投多了就會發現自己比較適合的缺，此時也可以再把履歷分成多個版本。

**3. 履歷投多少才夠？**

根據以往的經驗法則大約是1%回覆率。若你拿到一個offer需要經歷5個面試，那大概就要投500個職缺。

**4. 怎麼有效投履歷？**

- **大公司 > 小公司**
- 內推 > 海投
- Day1投履歷

很多大公司的職缺並不會同步更新在Job Board上，我的作法是把每家公司的career site都收錄進書籤，每天早上看一遍。

**5. 內推人去哪找？**

- [歹丸郎內推網路](https://brianhsublog.blogspot.com/2019/03/internalReferralAndTaiwanNetwork.html)
- [一畝三分地上的內推版](https://www.1point3acres.com/bbs/forum-198-1.html)
- LinkedIn詢問學長姐、前輩或陌生人，撰寫方法可參考歹丸郎內推網路文中格式

有疑問歡迎聯繫我，你的問題可以幫助我更新FAQ，解決更多同學的疑問！

## 前輩分享
1. [岷錡學長的找工分享(2022)](https://medium.com/mencher-publication/2022-new-grad-%E5%BE%8C%E7%96%AB%E6%83%85%E6%99%82%E4%BB%A3%E6%89%BE%E5%B7%A5%E4%BD%9C-e849769885e2)
2. [科技讀蟲的找工分享](https://yhtechnote.com/software-engineer-in-the-us/)

## 參考資源
1. [戰略幫手 - 山景城王同學](https://www.youtube.com/@chaowangmountainview)
2. [內推幫手 - 歹丸郎內推網路](https://brianhsublog.blogspot.com/2019/03/internalReferralAndTaiwanNetwork.html) [表單](https://docs.google.com/spreadsheets/d/1r5APlfg2XUV0RtN1yj_Be_VoicjwTdYxaHibiPeRwiQ/edit?gid=897958547#gid=897958547)
3. [刷題幫手1 - Neetcode](https://www.youtube.com/c/neetcode)
4. [刷題幫手2 - Cracking FAANG](https://www.youtube.com/@crackfaang)
5. [面試幫手 - 一畝三分地面試考古版](https://www.1point3acres.com/bbs/tag/%E6%B5%B7%E5%A4%96%E9%9D%A2%E7%BB%8F-6-1.html)
6. [BQ幫手1 - BQ寶典](https://www.1point3acres.com/bbs/thread-895663-1-1.html)
7. [BQ幫手2 - 不錯的BQ回答範例](https://www.youtube.com/@JeffSu)
8. [0到100的軟體工程師面試之路](https://ithelp.ithome.com.tw/users/20152262/ironman/5615?page=1)