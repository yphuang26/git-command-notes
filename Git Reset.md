
## Git Reset
---
Git reset 主要用於重置當前 HEAD 到指定狀態，有三種模式:
1. `--soft` : 最溫和的重置
    1. 只移動 HEAD 指針
    2. 保留所有變更在暫存區 (staged)
    3. 適合當你想要保留檔案修改，但要重新組織 commit 時使用
    4. 檔案狀態: 修改保留且已 staged
```bash
git reset --soft HEAD~1
```
2. `--mixed` : 預設模式
    1. 移動 HEAD 指針
    2. 清空暫存區，但保留檔案修改
    3. 檔案狀態: 修改保留但未 staged
```bash
git reset HEAD~1
```
3. `--hard` : 最強硬的重置
    1. 移動 HEAD 指針
    2. 清空暫存區
    3. 完全丟棄所有修改
    4. 檔案狀態: 修改全部丟棄
```bash
git reset --hard HEAD~1
```
### 取消 add
```bash
# 取消特定檔案
git reset ${FILE_NAME}

# 取消所有 add 的檔案
git reset

# 或者使用
git restore --staged ${FILE_NAME}
```
### 取消 commit
```bash
# 取消最後一次 commit，保留修改的檔案
git reset --soft HEAD^

# 取消最後一次 commit，丟棄修改的檔案
git reset --hard HEAD^

# 取消前 N 次 commit，保留修改
git reset --soft HEAD~N

# 修改最後一次 commit 的訊息
git commit --amend
```
### 取消 push
```bash
# 先重置到想要的版本
git reset --hard HEAD^    # 取消一個版本
git reset --hard HEAD~N   # 取消 N 個版本

# 然後強制推送
git push --force-with-lease origin ${branch_name}

# 或者更強硬的方式(不建議在協作專案中使用)
git push -f origin ${branch_name}
```
- 取消 push 時:
    - 優先使用 `--force-with-lease`
    - 可以避免覆蓋他人的提交
    - 在團隊協作時要特別小心
