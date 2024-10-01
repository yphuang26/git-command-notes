
### 查看目前分支
```shell
# 查看目前分支
git branch
# 列出所有分支
git branch -a
# 新增分支
git brnach {new_branch_name} # 在後面加上新分支的名稱(但不會切過去)
# 改分支名稱
git branch -m {old_name} {new_name}
```
### 更新 Repository
- 只同步最新的變更到本地 repository
```shell
git fetch
```
- 同步變更並清理不存在的遠端分支到本地 repository
```shell
git fetch --prune
```
## 切換分支
---
```shell
git checkout {branch_name}
```
- 如果遇到 error
```shell
# 查看變更過的資料
git status
# 查看文件被改過的地方
git diff test.py
# 如果有修改，最快的方式是改名
mv test.py test1.py
```
### 切換遠端分支的方式
- 創建一個名為 `dev` 的本地分支，並將其設置為追蹤 `origin/dev` 分支
```shell
git checkout -b dev remotes/origin/dev
```
- 不想創建新的本地分支，只是暫時進入遠端 `dev` 分支狀態
```shell
git checkout remotes/origin/dev
```
- 只想檢出一個臨時的分支來查看遠端分支的內容 (進入一個 '分離頭指針' (detached HEAD) 狀態，可以自由查看和修改文件，但這些修改不會直接影響任何分支)
```shell
git checkout --detach remotes/origin/dev
```
### 將原分支更新的內容更新到新的分支
```shell
git checkout dev # dev 為原分支
git pull # 確保 dev 為最新
git checkout dev_branch # dev_branch 為從 dev 切出的分支
git merge dev
git push # 更新到 dev_branch
```
## 刪除分支
---
```shell
# Delete Local Branch
git branch -d {branch_name}
git branch -D {branch_name}

# Delete Remote Branch
git push {remote_name} --delete {branch_name}
# example: git push origin --delete dev_test
```
### 合併分支
---
- 從 `master` 分支開了一個 `dev` 分支，做了 commits
- 要用 `master` 分支來合併 `dev` 分支
```shell
git checkout master # 切回 master 分支
git pull # 確保 master 分支是最新的
git merge dev # 合併分支
```
