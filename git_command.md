1.整个大体结构：
    工作区：我们能看到的项目目录
    版本库：
        暂存区：Stage或者时Index
        分支：git自动创建的master分支
        HEAD指针：只想master分支的指针
    git add命令实际上就是把要提交的所有修改放到暂存区（Stage），然后，执行git commit就可以一次性把暂存区的所有修改提交到分支

2.版本回退：
    git status:可以查看工作区的状态
    git log:展示提交历史记录（commit id这就是版本号,author,data,change）；git log --pretty=online美化输出(commit id,change)
    git reset --hard HEAD^：回退到上一个版本，^^这就是上两个版本，HEAD~number
    git reset --hard commit_id(前几位就行):直接回退或者穿梭到这个id对应的版本，
    git reflog:记录每一次命令,找到对应的修改的版本，比git log要丰富一点



3.管理修改：git实际上管理的是修改而不是文件，增加，删除，修改，新建他都是“修改”；
           commit只能将暂存区的修改提交到版本库

4.撤销某个文件（file）的修改：
    场景1：当你改乱了工作区某个文件的内容，想直接丢弃工作区的修改时，用命令git checkout -- file。
    场景2：当你不但改乱了工作区某个文件的内容，还添加到了暂存区时，想丢弃修改，分两步，
           第一步用命令git reset HEAD <file>，就回到了场景1，第二步按场景1操作。
    场景3：已经提交了不合适的修改到版本库时，想要撤销本次提交，参考版本回退一节，

5.删除文件(如果没有添加到版本库就被删了就无法复原)
    场景1：确实是要删除，先git rm file，然后git commit -m "XXX"
    场景2：误删，git checkout -- file,git checkout其实是用版本库里的版本替换工作区的版本，
           无论工作区是修改还删除，都可以“一键还原”