###windows下git 登录并搭建个人网站
github命令行登录
登录
关联用户名与邮箱
git config --global user.name "YOUR NAME"
git config --global user.email "YOUR EMAIL ADDRESS"
利用命令行在本地产生密钥
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
然后将你的github 的rsa_key放到github账户中

建立基本网站
Go to the folder where you want to store your project, and clone the new repository:

~$git clone https://github.com/username/username.github.io

Enter the project folder and add an index.html file:

~$cd username.github.io
~$echo "Hello World" > index.html

Add, commit, and push your changes:
git add --all
~$git commit -m "Initial commit"
~$git push -u origin master