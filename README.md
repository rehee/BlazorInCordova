# Blazor In Cordova

这个项目的想法是在学习blazor的时候突然想到为什么不能吧blazor扔进cordova里面呢. 看到微软的路线图,混合应用也在线路里面所以我想尝试一下. 网上搜索了一下 发现已经有大哥在多年前就尝试过了https://medium.com/@bickellukas98/blazor-cordova-a3b0a6c3bf10. 遇到了不少坑但是也成功了. 我在想这个已经是好多年之前了. 所以我想尝试一下.

## 步骤
1. 创建一个新的blazor assemby 项目
2. 在项目中创建一个cordova项目
3. 对比cordova的www下的index.html, 发现有一个引用cordova.js 的引用. 将其添加到blazor的wwwroot\index.html下
4. 通过上面大哥的研究, 需要将 index.html 的baseb标签移除.
5. 在program.cs中的httpclient的注入的baseaddress取消. 因为如果在electron中baseaddress是file 会出错.
6. 我的方法是在index中添加fetch 读取文件在callback回来
7. index.razor 的路由需要修改为 "/index.html"

以release的方式发布至文件. 将发布的文件的wwwroot的文件夹拷贝至cordova的www目录并覆盖源文件. build cordova. 这里因为条件所限只能使用eletron.

cordova的platinum electorn build 里面找到做好的程序 运行.

这个项目代码拿下来后

1. 以debug的方式build
2. publish到文件夹
3. 在dist路径下面会出现安装包
4. 如果dist没有再运行几次或者手动运行.

希望有小伙伴可以测试一下安卓和ios. 安卓不知道_还是不是不能用的. 如果不改名字的话不知道添加.nojekyll 是否可行

有其他问题请联系我.
