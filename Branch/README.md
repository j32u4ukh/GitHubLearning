# 他人新建分支

當其他合作者在他的本機建立了新的分支(分支名稱：UI)，並上傳 GitHub 之後，雖然  GitHub 上看的到，但透過`git pull origin master`下來後卻看不到。

###### 利用`git branch -v`查看本機分支
![不做處理，直接 pull 的結果](/Branch/first_pull.PNG)

這也是很正常的，新的分支也就不叫做 master 嘛。

## 解決方法

使用`git fetch --all`更新 "所有" remote 底下的分支。

`git fetch <remote name>`這個指令一次只能更新一個 remote。

如果你的專案底下有多個 remote，而且全部都想要更新的話，就可以使用這個指令。

###### 利用`git fetch --all`更新
![git fetch --all 的結果](/Branch/fetch_all.PNG)

###### 再次利用`git branch -v`查看本機分支
![結果看起來與直接 pull 的結果，故偷懶用同一張圖](/Branch/first_pull.PNG)

會發現分支數量還是跟之前一樣只有 6 個，此時可利用`git branch -a`查看包含遠端的所有分支。

###### 利用`git branch -a`查看包含遠端的所有分支。
![git branch -a 的結果](/Branch/branch_a.PNG)

可以看到其實已經將遠端分支抓下來了，而且從"利用`git fetch --all`更新"這張圖最後兩行也看到，本地的 UI 分支也建立好了。

現在該做的就是勇敢地跳到新的分支。

###### 利用`git checkout UI`跳到 UI 分支。
![git branch -a 的結果](/Branch/branch_a.PNG)

###### 再次利用`git branch -a`和`git branch -v`查看所有分支
![無論 -a 還是 -v，都出現 UI 分支](/Branch/branch_av.PNG)

