####WordPress建立博客遇到的各种问题
- unable to create directory wp-content/uploads. is its parent directory writable by the server   (图片无法上传的问题)

解决方案：由于html下的wp-content的权限问题，将权限修改为777就可以了
`root#chmod -R 777 /var/www/html/wp-content`
权限修改完后插件以及主题也可以自动更新了，不需要手动更新。（这是非常省力的一件事情）

- - -

-  固定连接，修改完成后需要手动修改下面的文件.htaccess

该文件的地址在wp-content/plugins/akismet/.htaccess

- - -
- wordpress更改永久链接url not found 404

```
设置自定义格式  
%year%
文章发表的年份，四位数，如 2004
%monthnum%
月份，如 05
%day%
天，如 28
%hour%
小时，如 15
%minute%
分钟，如 43
%second%
秒，如 33
%postname%
文章标题的别名 (编辑文章/页面时的别名栏)。对于文章标题为 “This Is A Great Post!” 的%postname%是this-is-a-great-post(查看 仅仅使用 %postname%)。 出于性能原因，强烈不建议使用%postname%作为链接地址的开头。 *** 注 - 从WordPress 2.0开始这条建议可以无视了。
%post_id%
文章的唯一ID，如 423
%category%
分类的别名 (新建/编辑分类时的别名栏)。 有层级关系的类型在链接地址里就像有层级的目录。 出于性能原因，强烈不建议使用%category%作为链接地址的开头。
%tag%
标签的别名(新建/编辑标签时的别名栏)。 出于性能原因，强烈不建议使用%tag%作为链接地址的开头。
%author%
作者的别名。
```
例如`/%year%/%monthnum%/%day%/%postname%/`
这样可能还会出错  `/index.php/%year%/%monthnum%/%day%/%postname%/`

第二种方法
（1）httpd.conf中
```
开启了对应的mode_rewrite模块：
把：
#LoadModule rewrite_module modules/mod_rewrite.so
改为：
LoadModule rewrite_module modules/mod_rewrite.so
```
(2)htdocs根目录下已经存在了.htaccess,且设置都已经正确(读写权限，以及拥有者)
.htaccess是控制固定链接的
（3）AllowOverride Not Enabled 
服务器可能没打开AllowOverride。
如果Apache中配置文件httpd.config的AllowOverride设置的是None，那.htaccess将被忽略
```
代码如下	
Directory /
Options FollowSymLinks
AllowOverride All
# Order deny,allow
# Deny from all
/Directory
```
也需要在DocumentRoot打开AllowOverride：
```
Directory “D:/wamp/www/” （这个取决于你的HTML文件放在哪里 ）
# Possible values for the Options directive are “None”, “All”,
# or any combination of:
# Indexes Includes FollowSymLinks SymLinksifOwnerMatch ExecCGI MultiViews
# Note that “MultiViews” must be named *explicitly* — “Options All”
# doesn’t give it to you.
# The Options directive is both complicated and important. Please see
# http://httpd.apache.org/docs/2.2/mod/core.html#options
# for more information.
Options Indexes FollowSymLinks
# AllowOverride controls what directives may be placed in .htaccess files.
# It can be “All”, “None”, or any combination of the keywords:
# Options FileInfo AuthConfig Limit
AllowOverride all
# Controls who can get stuff from this server.
# onlineoffline tag – don’t remove
# Order Allow,Deny
# Allow from all
/Directory
```
修改完后需要重启apache 服务

`root#service httpd restart ` 当然以上是基于你的http服务器是Apache，如果是nginx,则配置可能会有所差别。