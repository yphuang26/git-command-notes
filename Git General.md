
## 新增、初始化 Repository
---
- 初始化目錄，讓 Git 對這個目錄進行版控
- 會在目錄裡建立一個 .git 目錄 (刪除 .git 目錄，Git 就對目錄失去控制權)
```shell
git init
```
- 設定 `user.name` 和 `user.email`
```shell
git config user.name "xxx"
git config user.email "xxx@gmail.com"
```
### 將本地 repository 加入 GitHub 新的 repository
```shell
# 在本地初始化 Git
cd /path/to/your/repo
git init
git remote add origin https://github.com/your-username/your-repo-name.git
# 將本地程式推送到 GitHub
git branch -M main
git add .
git commit -m "Initial commit"
git push
```
```shell
# 或使用以下指令推送
git push --set-upstream origin main
```
這個指令會做兩件事:
- 將本地的 `main` 分支推送到遠程倉庫的 `origin` 倉庫中的 `main` 分支
- 設置 `main` 分支的上游分支為 `origin/main` ，以後當執行 `git push` 或 `git pull` 時，不再需要手動指定遠程分支
## 修改、更新到 GitHub repository
---
- 查詢目前狀態
```shell
git status
```
- 把檔案交給 Git
```shell
git add test.py # 讓 Git 開始追蹤 test.py 檔案 (把檔案加到暫存區)
git add .
```
- 把暫存區內容提交到倉庫
```shell
git commit -m "Initial commit" # Git 每次 commit 只會處理暫存區 (staging area) 裡的內容
```
### 修改、更新到 GitHub 步驟
```shell
git add app/routers/test.py
git commit -m "Update test.py with latest changes"
git push
```
## 刪除、更新到 GitHub repository
---
- 先刪除再 commit
```shell
rm test.py
git add test.py # 把這個「修改」加到暫存區
git commit -m "delete test.py"
```
- 使用 `git rm` 刪除 (會直接加到暫存區，不需要再 add 一次)
```shell
git rm test.py
```
- 只是不再讓 Git 控管 (沒有真的刪掉檔案)
```shell
git rm test.py --cached
```