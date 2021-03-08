## 刪除本地分支
// 使用 git branch -d <branch>

// 以刪除本地的 test_branch 分支為例

$ git branch -d test_branch

### 若所在的分支(例如 master)沒有將要刪除的分支合併(merge)進來，則要使用大寫 D
// 使用 git branch -D <branch>

// 以刪除本地的 test_branch 分支為例

$ git branch -D test_branch

## 刪除遠端分支
// 使用 git push <remote name> :<branch name> 

// 以刪除遠端的 origin remote 的 test_branch 分支為例，將會把 github 上的倉庫的分支刪除

$ git push origin : test_branch

## 刪除本地的遠端追蹤分支
// 遠端追蹤分支：位於本地，可追蹤至遠端分支的本地分支

// 使用 git branch -a 可以看到別人建立的分支(紅字呈現)，若 github 的倉庫已將該分支刪除，而自己的本地端尚未刪除

// 可以使用 git branch -rd <remote name>/<branch name> 刪除

// 以刪除本地的 test_branch 遠端追蹤分支為例

$ git branch -rd origin/test_branch

## 刪除 Remote Branch 鏈結

透過 `git fetch --all` 取得他人建立的分支後，在本地會有 Remote Branch 對應著伺服器中的分支。

當本地與伺服器中的分支被刪除後，透過 `git branch -a` 還是會看到 remotes/origin/XXX 的存在，

該紀錄原本是用於告訴本機 git 遠端的倉庫位置，但它不知道遠端已經被刪除，因此該紀錄還被留著。

可利用 `git fetch -p` 更新 git 與 github 之間的連結。

![操作流程](/Branch/git_fetch_p.png)

參考: [網站1](https://blog.yowko.com/git-delete-remote-branch/)
