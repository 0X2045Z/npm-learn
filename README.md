# npm-learn
## 基础
- 官网：https://www.npmjs.com/
- npm是前端工程师使用最多的代码管理仓库
## npm与node.js的关系
- NPM是随同NodeJS一起安装的包管理工具，能解决NodeJS代码部署上的很多问题，常见的使用场景有以下几种：
- 允许用户从NPM服务器下载别人编写的第三方包到本地使用。
- 允许用户从NPM服务器下载并安装别人编写的命令行程序到本地使用。
- 允许用户将自己编写的包或命令行程序上传到NPM服务器供别人使用。
- 由于新版的nodejs已经集成了npm，所以之前npm也一并安装好了。同样可以通过输入 "npm -v" 来测试是否成功安装。
- 随着Node.js火爆之后，npm也成为了前端工程师发布代码的仓库

## 安装node.js & npm
- npm会随着node.js一起安装
- 下载node：http://nodejs.cn
- 查看安装版本  
  node -v
- 查看安装版本  
  npm -v
- 全局重新安装npm  
  npm install npm -g
- 使用npm下载安装代码，仓库中出现  
  node_modules , package-lock.json

## npm指令，源切换
- 查看当前下载地址  
  npm get registry
- 设置为淘宝镜像  
  npm config set registry https://registry.npmmirror.com 
- 还原默认源  
  npm config set registry https://registry.npmjs.org
## npm指令，安装代码库
- 安装最新版本  
  npm install -g xxx
- 安装指定版本  
  npm install -g xxx@1.0.0
- 安装到当前文件夹  
  npm install xxx
- 安装指定版本到当前文件夹  
  npm install xxx@1.0.0
- 项目依赖安装， 并写入package.json的dependencies中  
  npm install –S xxx
- 同上面效果一样  
  npm install xxx
- 项目依赖安装，并写入package.json的devDependencies中  
  npm install –D xxx

### ** npm install默认不加或者 -save, 依赖放在package.json文件中的dependencies作为运行时依赖；npm install 加 -D 或者 -save-dev, 依赖放在package.json文件中的devDependencies作为开发时依赖  
  
- 项目本次安装依赖，临时使用淘宝镜像  
  npm install --registry=https://registry.npmmirror.com
- 安装某个依赖包（下面命令指定了版本@1.0.0），临时使用淘宝镜像  
  npm install XXX@1.0.0 --registry=https://registry.npmmirror.com
## npm指令，更新
- 检查更新，红颜色标记的就是可以更新的包，黄色标识不可更新的包  
  npm outdated    
- 执行更新(只会更新补丁版本或次版本，不会更新主版本)，如果不清楚主次版本，下面有版本号说明，请下拉  
  npm update  
- 方法一
- 1.安装"npm-check-updates"模块  
npm install -g npm-check-updates  
- 2.检查可更新的模块  
ncu  
npm-check-updates  
- 以上两条命令都可检查可更新模块。接下来更新package.json的依赖包到最新版本： 

- 方法二
- 全局安装  
npm-check  
npm install -g npm-check  
- 查看可更新的依赖  
npm-check  
- 更新依赖  
npm-check -u  
- 方发三
- 更新主版本的另一种方式就是先卸载，再重新安装  
- 卸载  
npm uninstall xxx  
- 重新安装-最新版本  
npm install xxx  
- 重新安装-制定版本  
npm install xxx@2.0.0  

- 升级 package.json 文件的 dependencies 和 devDependencies 中的所有版本  
ncu -u  
以上命令执行，更新全部模块。但在实际开发中不建议一次全部更新，可以根据实际需要，更新指定的模块，并且可以根据作用范围在后面加上 -D、-S 或 -g  

## npm指令，卸载
- 卸载  
  npm uninstall <package-name>  
- 使用 -S 或 --save 标志，则此操作还会移除 package.json 文件中的引用  
  npm uninstall -S <package-name>  
- 如果程序包是开发依赖项（列出在 package.json 文件的   devDependencies 中），则必须使用 -D 或 --save-dev 标志从文件中移除  
  npm uninstall -D <package-name>   
- 卸载全局依赖  
  npm uninstall -g <package-name>   
## npm指令，查看
- 查看全局包版本  
  npm list -g --depth 0
- 查看某个包的版本  
  npm list vue-cli
### npm依赖包版本号，npm 版本号形式 X.Y.Z 表示：主版本号.次版本号.修订号，版本号递增规则如下： X. 主版本号：当你做了不兼容的 API 修改， Y. 次版本号：当你做了向下兼容的功能性新增， Z. 修订号：当你做了向下兼容的问题修正

## 依赖库版本号、符号
- 没有任何符号  
  1.0.0  
  完全百分百匹配，当前库/项目必须使用当前版本号，如果和其他依赖使用了相同库不同版本，会在库的文件夹下建立一个 node_modules 文件夹存放它需要依赖的版本文件。
- ~  
  不改变主版本号和次版本号，修订号可以随意更改  
  例如 ~2.0.0 ，可以使用 2.0.0、2.0.2 、2.0.9 的版本。
- ^  
  不改变主版本号（主版本号非0），此版本号和修订号可以随意更改  
  例如 ^2.0.0 ，可以使用 2.0.1、2.2.2 、2.9.9 的版本。
- // *  
  星号表示任意版本 对版本没有限制， 一般不用  
  "base": "*"
- // >  
  大于某个版本，表示只要大于这个版本的安装包都行  
  例如："node": "> 4.0.0"
- // >=  
  大于某个版本，表示只要大于或等于这个版本的安装包都行  
  例如："node": ">= 4.0.0"  
- <=  
  小于或等于某个版本，表示只要小于或等于这个版本的安装包都行  
  例如："http-proxy-middleware": "<=0.17.3"  
- // -  
  -表示两个版本号之间的版本  
  "base": "1.0.1-1.5.9"  
  例如 1.0.1-1.5.9 可以使用 1.0.1到1.5.9之间的任意版本  









