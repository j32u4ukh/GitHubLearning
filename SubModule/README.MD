# submodule

Submodule (子模組) 其實是個很常見的概念，在專案中想要引入其他專案的代碼，亦或是第三方的函式庫，被引入的庫就可以被看為是一個子模組。

## 使用時機

當一個套件被你的多個專案都引用時，就可以考慮把這個套件獨立出去，再做為 submodule 引入進各別專案。

又或是第三方套件沒辦法利用 pip 安裝時，也可以透過 submodule 的形式來引入。

當上述兩種情況的套件更新了程式碼，使用到這些套件的專案如何更新呢？難道是重複步驟把檔案複製到原來地方嗎？這樣會不會太麻煩，這時候就是需要 git submodule 來幫助大家進行程式碼的更新，這樣隨時隨地都可以取得最新的程式碼。

## 建立 submodule

建立 Submodule 的語法如下，

```
$ git submodule add [<options>] [--] <repository> [<path>]
```

實際範例:

![建立 Submodule](/SubModule/add_submodule.png)

* 最後面的 `[<path>]` 是可以自行對 clone 下來的 submodule 資料夾命名，若無 `[<path>]` 則會以專案本身名稱作為資料夾名稱。
* 不要手動建立上述資料夾，否則會產生衝突。

下面示範在執行指令的資料夾之下，再建立 submodule 資料夾，其中再建立 repo 資料夾。

```
$ git submodule add https://github.com/j32u4ukh/Xu3.git submodule/repo
```

## 建立完成後

我們可以使用 `$ git status` 來查看現況，如下圖。

![建立完成後](/SubModule/after_add_submodule.png)

 .gitmodules，裡面紀錄 submodule 的對應關係，我們實際打開看內容:
 
 ```
 [submodule "Xu3"]
	path = Xu3
	url = https://github.com/j32u4ukh/Xu3.git
  ```
 
 * 可以使用 `git submodule status` 查看目前 submodule 的狀態
 
 回去看 github 網站就會多出一個小圖示了
 
 ![Submodule on github](/SubModule/submodule_on_github.png)
 
## 提交子模組更新

git Bash 進入子模組的資料夾後，會發現就和一般用 git 做版本控制的資料夾一樣，可以用 `git add .` 或 `git push origin master"` 等指令。

子模組有更動需要提交，請依照步驟如下:

1. 提交子模組更動
2. 上傳到子模組的遠端儲存庫
3. 提交上層專案更動
4. 上傳到上層專案的遠端儲存庫

### 批次更新子模組

個別 repo 更新比較麻煩，必須到個別的目錄底下執行 git pull 去拉 upstream 的程式碼，可是這樣會比較安全；
若要一次全部更新所有的 submodule 可以用這 foreach 指令：

```
git submodule foreach --recursive git pull origin master
```


## 移除子模組

要移除子模組有點麻煩，一共 7 個步驟 ([參考1](https://git.wiki.kernel.org/index.php/GitSubmoduleTutorial#Removal), [參考2](https://kaddopur.github.io/blog/2017/05/15/git-submodule/))

1. 刪掉 .git/config 中相關的段落
2. 刪掉 .gitmodules 中相關的段落
3. 暫存 .gitmodules 的更動
4. 用 git rm --cached 停止追蹤子模組
5. 刪掉 .git/modules/<submodule>
6. 提交更新
7. 真正把子模組刪除

實際的指令如下，每步一行

```
$ git submodule deinit submodule/repo
$ vi .gitmodules
$ git add .gitmodules
$ git rm --cached submodule/repo  # 後面不帶 '/'
$ rm -rf .git/modules/submodule/repo
$ git commit -m 'remove repo'
$ rm -rf repo
```
 
 ## 複製包含子模組的專案
 
直接 git clone 上層專案，你會發現子模組的資料夾存在但卻是空的。此時你要先運行

```
$ git submodule init
```

這個指令會將你在 .gitmodules 中的子模組設定寫入 .git/config 中，接下來再運行

```
$ git submodule update [--recursive]
```

這個時候子模組才會真正被下載下來，[--recursive] 的 [] 表示可加可不加。

### 連帶 submodule 一起抓下來
包含 submodule 的 submodule。

```
$ git clone --recursive https://github.com/j32u4ukh/Xu3.git
```

## 參考網站:

1. [蝌蚪伯的摳頂筆記](https://kaddopur.github.io/blog/2017/05/15/git-submodule/)
2. [twtrubiks/Git-Tutorials](https://github.com/twtrubiks/Git-Tutorials/blob/master/git_submodule_turorial.md)
3. [Git Submodule 用法筆記](https://blog.chh.tw/posts/git-submodule/)
4. [Git Submodule 介紹與使用](https://blog.wu-boy.com/2011/09/introduction-to-git-submodule/)
