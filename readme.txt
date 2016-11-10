git远程仓库
注册github帐号，由于本地Git仓库和github仓库之间的传输是通过SSH加密的，所以需要一点设置：
第一步：创建SSH key，在用户主目录下，看看有没有.ssh目录，如果有，再看看这个目录下有没有id_rsa和id_rsa.pub这两个文件，如果有的话，直接跳过如下命令，如果没有的话，打开命令行，输入如下命令：
ssh-keygen -t rsa -C "youremial@example.com"
注意：id_rsa是私钥，不能泄漏出去，id_rsa.pub是公钥，可以放心告诉任何人
第二步：登录github，打开“Setting”中的SSH Keys页面，然后点击“Add SSH Key”，填上有意义的title，在Key文本框里粘贴id_rsa.pub文件内容
点击Add Key，就可以看到已经添加的key了

如何添加远程库？
首先，登录github，然后在右上角找到“create a new repository”创建一个新的仓库
在repository name填入项目名称，其他保持默认设置，点击Create repository按钮，就成功创建了一个新的Git仓库了

Github上的这个仓库还是空的，github告诉我们，可以从这个仓库克隆出新的仓库，也可以把一个已有的本地仓库与之关联，然后，把本地仓库的内容推送到github仓库。
现在根据github的提示，在本地的learngit仓库下运行命令：
git remote add origin https://github.com/AliceSteven/learngit.git
把本地库的内容推送到远程，使用git push命令，实际上是把当前分支master推送到远程

由于远程库是空的，我们第一次推送master分支时，加上-u参数，Git不但会把本地的master分支内容推送到远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令。推送成功后，可以立刻在github页面中看到远程库的内容和本地一模一样了，上面过程中要输入github的用户名和密码。
从现在起，只要本地做了提交，就可以通过如下命令：
git push origin master
把本地master分支的最新修改推送到github上了。

git创建与合并分支

如何解决冲突