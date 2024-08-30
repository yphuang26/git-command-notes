
## Cherry-Pick
---
cherry-pick 顧名思義是<span style="color:rgb(0, 176, 80)">只撿取特定的 commit 放到目前的分支上</span>。
一般來說，整體開發會有一條穩定版本 (master 或 release)，開發者再開其他分支 (dev) 做修改、合併。但有時會突然來個臨時功能需要修復或新增，這個時候又不想把整個分支dev合併進master時，就可以使用cherry-pick，只挑自己想要的commit合併到master就好。
### 使用方法
Example: cherry-pick `feature/new_func` commit into `dev` 
1. check `feature/new_func` commit hash
```shell
git checkout feature/epc_support_git
git log
```
2. cherry-pick commit hash `abc1234` into `dev` 
```shell
git checkout dev
git cherry-pick abc1234
```
Example: cherry-pick commits
- cherry-pick commits from `def5678` to `ghi9012` (include `ghi9012` )
```shell
git cherry-pick def5678^..ghi9012
```
