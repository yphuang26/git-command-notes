
## Git 解衝突
---
要將 `feature/new-feature` 的更新 merge 到 `origin/dev` 分支 (但兩個分支都分別在同個文件做過不同更新，因此會遇到 conflicts)。
### 完整流程
---
首先，若工作目錄中有未提交的修改，先暫存起來:
```
git stash
```
確定工作目錄是乾淨的 (即沒有未提交的修改) 後:
```
# 1. 切換並更新基準分支
git checkout dev
git pull origin dev

# 2. 切換回功能分支
git checkout feature-branch

# 3. 執行 Rebase (這一步可能產生衝突)
git rebase dev
```
遇到衝突時的處理:
```
# 4. 檢查衝突
git status

# 5. 手動編輯所有衝突檔案，移除衝突標記(<<<<<<<, =======, >>>>>>>)

# 6. 標記衝突已解決(不需要 commit)
git add .

# 7. 繼續 rebase
git rebase --continue

# 如果有多個衝突點，重複執行 4~7 步驟，直到 Rebase 完成
```
Rebase 完成後的處理:
```
# 8. 檢查變更是否正確

# 9. 將新的歷史推送到遠端 (必須強制推送，因為 Rebase 改變了歷史)
git push -f origin feature-branch
```
若前面有 `git stash` ，要再 pop 出來:
```
git stash pop
```
