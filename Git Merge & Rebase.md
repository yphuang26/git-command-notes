## Git Rebase
---
`git rebase` 是將一個分支的變更應用到另一個基礎分支之上。相當於將目標分支中的變更暫時抽出，然後重新應用在另一個分支的基礎上。會創建一個新的提交歷史。
### 使用方法
Example: Rebase `dev` into `feature/create_new_func` 
1. Update local dev branch
```shell
git checkout dev
git pull
```
2. Rebasing
```shell
git checkout feature/create_new_func
git rebase dev
git push
```
#### 優點
- 清晰的歷史: 重新提交歷史，避免了合併提交 (merge commit)
- 單一提交點: 所有的提交點會被重新排列，使提交歷史簡潔
#### 缺點
- 複雜性: 如果在重寫的過程中出現衝突，解決衝突會比較複雜
- 潛在風險: 在公開的分支上重寫歷史可能會導致問題，因為其他人可能基於原始歷史進行了工作
## Git Merge
---
`git merge` 是將兩個分支的歷史合併在一起，創建一個新的合併提交 (merge commit)，保持兩個分支的歷史不變。
### 使用方法
Example: Merge `dev` into `feature/create_new_func` 
1. Update local dev branch
```shell
git checkout dev
git pull
```
2. Merging
```shell
git checkout feature/create_new_func
git merge dev
git push
```
####  優點
- 簡單直接: 合併的過程比較簡單，如果出現衝突也容易解決
- 完整的歷史: 保留了所有提交的歷史，便於追蹤變更
#### 缺點
- 歷史複雜: 合併提交可能會使提交歷史變得複雜，特別是有多個合併提交時
- 合併提交: 每次合併都會創建一個新的合併提交，可能會增加歷史的噪音
## Reference
---
- [Git Rebase 與和 Git Merge 做合併分支的差異](https://medium.com/starbugs/git-%E6%88%91%E4%BB%A5%E7%82%BA%E7%9A%84-git-rebase-%E8%88%87%E5%92%8C-git-merge-%E5%81%9A%E5%90%88%E4%BD%B5%E5%88%86%E6%94%AF%E7%9A%84%E5%B7%AE%E7%95%B0-cacd3f45294d)
