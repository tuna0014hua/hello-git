# Git & github 操作練習

## **2021/09/18 筆記**

**A. git 介紹**

- git 是一個**分散式版本控制**軟體
- 最初目的是為更好地管理 Linux 核心開發而設計
- 由 Linux 之父(Linus Torvalds)所開發

**B. 安裝 git (widows 版)**

1. 先確認電腦是否有安裝過 git:
   - step 1: 檢查 cmd (命令提示字元)
   - step 2. 輸入下方指令

```
git --version
```

2. [git 安裝檔](https://git-scm.com/download/win)

   - 提示: 安裝路徑中不要有中文字，容易出錯。

**C. git bash 指令**
| Windows | MacOS/Linux | 說明 |
| ------- | ----------- | ---- |
| cd | cd | 切換目錄 change directory |
| pwd | pwd | 顯示目前所在的路徑 |
| mkdir hello-git| mkdir hello-git| 建立新資料夾 make dir 後接檔案名稱|
| ls/dir | ls | 列出目前檔案夾的檔案列表 list |
| ls -a | ls -a | 出全部檔案（列出隱藏檔） |
| ls -l | ls -l | 以完整格式列出檔案 |
| ls -al | ls -al | 以完整格式列出所有的檔案 |
| touch test.txt| touch test.txt| 建立新檔案後接檔案名稱 |
| rm/del | rm | 刪除檔案 remove |
| cat test.txt| cat test.txt| 印出檔案內容後接檔案名稱 |
| copy | cp | 複製檔案 copy |
| move | mv | 移動檔案 move |
| cls/clear | clear | 清空畫面上的內容 |

```
note:
. 現在的檔案位置
.. 回到上一層
~ 使用者的目錄 ex:「/user/aaa」...
* 全部
/ 根目錄

cd ~ -> 回到使用者目錄或是 home 目錄
cd .. -> 回到上一層

-a -> all全部
-f -> force 強制
-r -> recursive 可以刪除每一層檔案夾

nano (test.txt)-> 直接在終端機編輯檔案
nano 存檔 ^(ctrl)+x -> y -> enter

指令: rm -rf * -> 強制刪除全部檔案(需小心使用)

```

**D. git 設定環境變數**

- 檔案位置： ~/.gitconfig
- 設定名稱： git config --global user.name "自訂使用名稱"
- 設定郵件： git config --global user.email "使用 github 的 email"
- 確認設定的內容: git config --list

**建立 repo**

> repository (存儲庫) --> repo

- 每一個專案的進度(版本)都是獨立控管

**git 指令**
| git 指令 | 說明 |
| ---- | --- |
| git init | 將目前的目錄初始化為 git 目錄, 建立本地儲存庫 |
| git config | 設定或檢視 git 設定檔資訊 |
| git status | 查看 git 的狀態 |
| git add test.txt | 將檔案加入 git 暫存區 後接檔案名稱|
| git commit -m "正確填寫這次 commit 的資訊"| 將暫存區的檔案提交至儲存庫納入版本控制 |
| git commit -am "xxxxx" | 針對已經加入過的檔案，可以直接用以下指令提交 |
| git diff | 檢視這次修改的差異 |
| git restore --staged login.html| 可以「反悔」加入暫存區|
| git restore login.html | 反悔剛剛的修改 |
| git checkout \<commit\> test.txt | 讓檔案回到某個特定版本 |
| git log | 查看提交紀錄 |
| git blame test.txt | 查看內容是誰編寫的 |
| git branch | 檢視分支 |
| git branch \<branch-name\> | 建立分支 |
| git switch \<branch-name\> | 切換分支 |
| git merge | 合併分支 |

```
note:
1. 將預設 master 分支 改為 main
指令: nano ~/.gitconfig
[init]
        defaultBranch = main
2. 將分支改成main
指令: git branch -m master main

```

**git status 檔案狀態**

- Changes to be committed（將要提交的檔案）
  - 透過 git add, rm, mv 轉移過來的檔案
- Changes not staged for commit（被更動但尚未要提交的檔案）
  - 都是先前就已經被提交過的檔案
- Untracked files（未被追蹤的檔案）
  - 意指完全新加入的檔案，不曾被提交過

**合併分支**

1. 先切換到主要合併的 branch

```
$ git switch main
```

2. 把另一隻寫好的分支合併到主分支去 main

```
$ git merge feature-login

```

## **2021/09/19 筆記**

**A.github repo**

1. 在 github 上建立一個 github repo

```
$ git remote add origin https/ssh
```

- remote: 遠端
- add: 增加
- origin: 是這個遠端的名字，可以不要叫做 origin，但我建議不要改
- 遠端 repo 的網址 : https /ssh
-

2. push: 將本地儲存庫內容推送到遠端儲存庫並要推到主分支裡

```
$ git push -u origin main

```

3. clone: 從遠端儲存庫 (github) 複製副本至本地儲存庫
   - 在 github 上建立一個 hello-node 專案，勾選建立 readme
   - 找到自己這個專案的 url，在 home 目錄下 clone 這個專案

```
$ cd ~
$ git clone <url>
```

4. pull: 將遠端儲存庫拉回合併更新到本地儲存庫

```
$ git pull = git fetch + git merge
```

> Pull 指令其實就是去上線抓東西下來（Fetch），並且更新本機的進度（Merge）

---

# NodeJS

- Node.js 是一個能執行 JavaScript 的環境
  - 以 V8 為核心，加上一系列 C/C++ 的套件，成功的讓 Server 端也可以執行 JavaScript
- Google Chrome 的 JavaScript 引擎，負責解析、執行 JavaScript
  - 負責實踐 ECMAScript 規範中定義的部份

**安裝方法**

- LTS: long-term support 長期維護版
- Current: 最新的、目前的
- Active LTS: 正在積極維護跟升級中的版本
- Maintenance LTS: 維護中的 LTS 直到生命週期結尾
- EOL: end of life

**windows 安裝流程與指令**

windows -> 電腦本身就有內建，只需裝啟用檔即可 (nvm-setup.zip)

1. $ nvm list available -> 列出可安裝版本
2. $ nvm install 14.17.6 -> 安裝最新版本
3. $ nvm list -> 列出你電腦裡 node 的版本
4. $ nvm use 14.17.6 -> 切換版本
5. $ node -v -> 確認目前 node 的版本
6. $ nvm alias default 14.17.6 -> 設定預設版本

---

# **前後端區分**

- 前端(Front-end): 使用者直接接觸的系統/畫面(介面)
- 後端(Back-end): 隱藏在前端後，協助處理邏輯運算&資料處理的程式
- 前台(Front-stage): 使用者看到的前端畫面
- 後台(Back-stage): 管理者看到的前端畫面功能

```
      request(請求)
      ------>                ------>
(html、css、js)   (node.js、php)     (MySQL)
user              web server         db
      <------                  <------
      response(回應)
```

---

![前後端運作流程](https://d1dwq032kyr03c.cloudfront.net/upload/images/20180319/20106865LdOqeQqH8b.jpg "前後端運作流程")
