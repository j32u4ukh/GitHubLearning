# Test123
`學習使用Git與GitHub`

* [將檔案從 Git 中移除](https://mtr04-note.coderbridge.io/2020/08/09/about-git-deletefile/)

```git
$ git filter-branch -f --tree-filter "rm -f (檔案的相對路徑)"
```

* [方法 2](https://cynthiachuang.github.io/Ignore-Tracked-Files-in-Git/)

```git
$ git rm --cached filename    
$ git rm -r --cached foldername 
```
