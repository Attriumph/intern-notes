
* 1.快速拉取远程分支并创建本地分支方法：

      git checkout -b 本地分支名 origin/远程分支名
      //在哪个分支创建，就是复制哪个分支去创建
* 2.push和pull命令总结：

      git push <远程主机名> <本地分支名>:<远程分支名>
      git pull <远程主机名> <远程分支名>:<本地分支名>

   **注意，分支推送或者拉取的顺序的写法是<来源地>:<目的地>** ,

  > 所以git pull是<远程分支>:<本地分支>，而git push是<本地分支>:<远程分支>。
如果省略远程分支名，则表示将本地分支推送与之存在”追踪关系”的远程分支(通常两者同名)，如果该远程分支不存在，则会被新建。
使用该方式会在本地新建分支，并自动切换到该本地分支。

  比如，要取回origin主机的next分支，与本地的master分支合并，需要写成下面这样 -

      $ git pull origin next:master

  如果远程分支(next)要与当前分支合并，则冒号后面的部分可以省略。上面命令可以简写为：

      $ git pull origin next

  >在某些场合，Git会自动在本地分支与远程分支之间，建立一种追踪关系(tracking)。

   >**同时，在git clone的时候，所有本地分支默认与远程主机的同名分支，建立追踪关系，也就是说，本地的master分支自动”追踪”origin/master分支。
Git也允许手动建立追踪关系。**

      $ git branch --set-upstream master origin/next
      //指定master分支追踪origin/next分支。

  查看upstream的情况，使用：

      $ git remote -v

   如果当前分支与远程分支存在追踪关系，git pull就可以省略远程分支名。

      $ git pull origin

  >上面命令表示，本地的当前分支自动与对应的origin主机”追踪分支”(remote-tracking branch)进行合并。
如果当前分支只有一个追踪分支，连远程主机名都可以省略。

      $ git pull

  > 上面命令表示，当前分支自动与唯一一个追踪分支进行合并。

  **如果合并需要采用rebase模式，可以使用–rebase选项。**

      $ git pull --rebase <远程主机名> <远程分支名>:<本地分支名>
  > rebase  就是在拉线上新代码，和你本地的整合到一起,相比merge，rebase会取消掉所有之前所有的commit提交
    rebase 的过程中尽量不要有其他操作，不要 commit merge 之类的，最好也不要 git rebase --abort 最好把当前 rebase 过程走完，再做其他操作


* 3.git 团队协作
    ##### 合并常用代码


      //从远程beta分支拉取最新代码，并和本地当前分支以rebase方式合并
      git pull --rebase upstream beta

      //返回到某个commit版本
      git reset --hard 1e3xxx  

      // 添加upstream，让本地分支和远程建立起追踪关系
      git remote add upstream https://github.xxx
      （git rebase upstream beta）


      //手动解决下冲突, 继续进行rebase
      git add .
      git rebase --continue
      git push origin <your_dev>

      //当代码混乱的时候，先用
      git reset --hard commit版本号 恢复到之前版本
      //再用一下命令合并
      git pull --rebase upstream beta


   #### 减少分支commit
     * commit --amend
     > 当commit的内容相近时，可以在 commit 的时候使用 git commit --amend 来合并当前
    commit 到上一个 commit 里，可避免每次修改都有一个 commit, 也有助于他人 review 代码
    * 多余的 commit log 可以用 git rebase -i xxx 给 fixup 掉

* 4.将创建的本地代码上传到Github上：
   * 在Github上new一个repository；

   * 进入本地的项目目录下，建立git仓库：

         git init

   * 将项目所有文件添加到仓库中：

         git add .

   * 将添加的文件提交到仓库：

         git commit -m "文件描述"

  * 将本地仓库关联到Github上：

        git remote add origin url_of_your_newrepository

  * 上传代码到Github远程仓库：

        git push -u origin master

 * 5.命令的“联动模式”
     > 当重复使用连续的几个命令时，可以使用“；”将多个命令写在一起

       git add -A;git commit --amend --no-edit; git push origin beta -f;

 * 6. merge和rebase

   #### merger有两种格式：
    * --no-ff指的是强行关闭fast-forward方式。

    > fast-forward方式就是当条件允许的时候，git直接把HEAD指针指向合并分支的头，完成合并。属于“快进方式”，不过这种情况如果删除分支，则会丢失分支信息。因为在这个过程中没有创建commit

    * git merge --squash
    > 是用来把一些不必要commit进行压缩，比如说，你的feature在开发的时候写的commit很乱，那么我们合并的时候不希望把这些历史commit带过来，于是使用--squash进行合并，此时文件已经同合并后一样了，但不移动HEAD，不提交。需要进行一次额外的commit来“总结”一下，然后完成最终的合并。

   >总结：
  --no-ff：不使用fast-forward方式合并，保留分支的commit历史
  --squash：使用squash方式合并，把多次分支commit历史压缩为一次

     #### rebase和merge的区别 ([原文在这里](https://www.cnblogs.com/xueweihan/p/5743327.html))
   * 采用merge和rebase后，git log的区别，merge命令不会保留merge的分支的commit：
   * 处理冲突的方式：
     > 使用merge命令合并分支，解决完冲突，执行git add .和git commit -m'fix conflict'。这个时候会产生一个commit。

     > 使用rebase命令合并分支，解决完冲突，执行git add .和git rebase --continue，不会产生额外的commit。这样的好处是，‘干净’，分支上不会有无意义的解决分支的commit；坏处，如果合并的分支中存在多个commit，需要重复处理多次冲突。

     #### 每次merge
    * 每一次merge前确认代码要 merge 的时候，没什么修改的了，记得要 git pull   --rebase xxx xxx 一下，因为可能你之前别人又 merge  了新的代码
    * 别人给了comit评论，自己修改完，push完之后，会自动对比生成新的changed files
## 7.git提交pr和issue注意点
1） 提的 pr 名字都统一叫：[NM]  主题XXX —— xxx nm 表示 no merge 的意思，名字统一这样关联 issue 的时候比较好看，知道这个 pr 做了什么，后面的
   xxx 表示当前修改的什么场景，小程序、app、pc 端、移动端等

2） issue pr 写的内容一样的话，那开一个 issue 就没有意义了，要么都写在 issue 里，要么写在 pr 里，且写的内容最好简单明了。
   简单列表一下具体修改什么了，如果有没完成的就用 checkbox 来写，如果都已经完成了，直接 - markdown 来写就可以了
   记住一点就是，易读啊。写完之后 preview 的时候，能很直观的看到你修改的内容，再提 pr 或 issue

## 8.其他小tips
 * 克隆完记得git add remote upstream 网址
 * git log 和git reset --hard commit版本号返回
 * 修改最后一次提交 $ git commit --amend
 * 压缩多次commit提交 git rebase -i HEAD~4
