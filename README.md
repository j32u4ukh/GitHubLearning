# Test123
學習使用Git與GitHub

# 在地資料夾上傳至GitHub，以Test123為例
# 先在GitHub建立好Repository，目前不知道能否在本機下指令去GitHub建立Repository
$ cd Desktop/Test123

# 指令會在Test123資料夾中建立檔案README.md
$ echo "# Practicing Git" > README.md

# 將資料夾轉為Repository，產生.git檔
$ git init

# 將README.md加入.git/index
$ git add README.md

# 將檔案寫入儲存庫，-m 後面的字串為工程師對此次commit做的描述，可自己決定內容
$ git commit -m "add README.md"

# 告訴git bash我要將檔案傳到遠端的哪裡，origin用來代表後面那串網址，用origin只是習慣
# 遠端位置形式分為HTTPS和SSH，本例為HTTPS
$ git remote add origin https://github.com/github帳號/repository名稱.git

# 上傳資料夾內容，把 master(現在位置的代稱，或現在這個分支)的內容，推向 origin(剛才指定的遠端位置)這個位置。
# 當初下完指令後出現：
  To https://github.com/github帳號/repository名稱.git
   ! [rejected]        master -> master (fetch first)
  error: failed to push some refs to 'https://github.com/github帳號/repository名稱.git'
  hint: Updates were rejected because the remote contains work that you do
  hint: not have locally. This is usually caused by another repository pushing
  hint: to the same ref. You may want to first integrate the remote changes
  hint: (e.g., 'git pull ...') before pushing again.
  hint: See the 'Note about fast-forwards' in 'git push --help' for details.
# 上網查的原因說是GitHub中的內容較本機內容新，因此無法上傳
$ git push -u origin master

# 解決辦法就是輸入git pull把線上內容(origin)和本機內容(master)這邊做整合。
$ git pull origin master

# 但又會發現error message如下：
  warning: no common commits
  remote: Counting objects: 3, done.
  remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
  Unpacking objects: 100% (3/3), done.
  From https://github.com/j32u4ukh/Test
   * branch            master     -> FETCH_HEAD
   * [new branch]      master     -> origin/master
  fatal: refusing to merge unrelated histories

# 上網找到的原因是：Git在2.9.0版以後，不允許合併沒有共同祖先的分支，需要加上--allow-unrelated-histories才不會出錯
$ git pull origin master --allow-unrelated-histories

# 終於可以上傳了~
$ git push origin master
