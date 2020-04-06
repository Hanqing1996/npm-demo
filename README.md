# npm笔记

#### 卸载用 npm 安装的 yarn
```
npx npm uninstall -g yarn
```

#### 那么应该怎么安装 yarn 呢
[用 yarn.msi](https://classic.yarnpkg.com/en/docs/install/#windows-stable)

#### 用 yarn 安装全局依赖
> npx 的作用是自动去找 yarn 的安装目录，如果不用 npx,你就要去yarn 的安装目录下执行 yarn global add @vue/cli@4.1.2
```
npx yarn global add @vue/cli@4.1.2
```
#### 用 yarn 卸载全局依赖
```
yarn global remove @vue/cli
```
#### npm info babel
查看 babel 的官方版本信息
    * latest:官方最新版本
    * next:官方下一个版本（计划中）
    * old:官方上一个版本

#### npm ls babel
查看本地项目 babel 版本信息 
```
$ npm ls babel
C:\Users\zhq\Desktop\test
`-- babel@5.8.38
```

#### npm init -y
* 有默认选项的 npm init
* yarn init -y 同理。推荐用这个

#### npm 原理
> 全局没有安装webpack-cli，也可以在package.json里面的script里面直接使用脚本名，不用加上路径。npm 脚本的原理非常简单。每当执行npm run，就会自动新建一个 Shell，在这个 Shell 里面执行指定的脚本命令。因此，只要是 Shell（一般是 Bash）可以运行的命令，就可以写在 npm 脚本里面。
比较特别的是，npm run新建的这个 Shell，会将当前目录的node_modules/.bin子目录加入PATH变量，执行结束后，再将PATH变量恢复原样。这意味着，当前目录的node_modules/.bin子目录里面的所有脚本，都可以直接用脚本名调用，而不必加上路径。比如，当前项目的依赖里面有 Mocha，只要直接写mocha test就可以了。

#### npmignore
> 用于在 npm publish 时去除多余文件
```
/docs/
/coverage/
/summary/
/src/
/tests/
/.idea/
babel.config.js
karma.conf.js
deploy.sh
.travis.yml
``` 

#### 其它
* 永远别用cnpm!!!!
* 配置淘宝npm镜像
```
npm config set registry https://registry.npm.taobao.org
npm config delete registry //销毁
```
* 如果一个包是给用户（用这个组件的程序员）使用的
```
npm i vue
```
* 如果一个包是给开发者使用的（-D表示给 developer 使用）,比如 chai
```
npm i -D parcel-bundler
```  
   
#### npm link   

#### npm root -g
显示全局安装的包的路径

#### npm init(npm install 前一定要npm init,因为npm install 不会自动生成 package.json)
* 生成package.json

#### npm install
* 按照package.json初始化项目
* 会把包放入node_modules目录
* package-lock.json 内容相比 package.json 有缺失时（cnpm 的坑），可用该命令更新 package-lock.json

#### npm install X -g
* 安装模块到全局，不会在项目node_modules目录中保存模块包。
* 不会将模块依赖写入devDependencies或dependencies 节点。
* 之后运行 npm install 初始化项目时不会下载模块X。
* 注意如果根目录中一开始没有package.json文件，那么运行 npm install（-D,-g...无所谓）会生成package.json文件

#### npm install X
* 会把X包安装到node_modules目录中
* x的版本将首先询问package.json，如果发现package.json中没有相关记录，则安装最新版本，但不会记录在package.json中
* 之后运行npm install 初始化项目时，不会自动安装X

#### npm install X --save
* 会把X包安装到node_modules目录中
* 若package.json中有相关记录，则按照记录安装对应版本
* 若package.json中没有相关记录，则安装最新版本，并在package.json的dependencies属性下添加X及安装版本

#### npm install -D X
* 会把X包安装到node_modules目录中
* 若package.json中有相关记录，则按照记录安装对应版本
* 若package.json中没有相关记录，则安装最新版本，并在package.json的devDependencies属性下添加X及安装版本
* 会生成一个package-lock.json

#### npm ci
* 从 package-lock.json 文件安装依赖
* 如果 package lock 里面依赖和 package.json 不一致， npm ci 会报错并且退出， 而不是更新 package lock 文件
* 它不会改变 package.json 或者任何 package-locks

#### npm run
* 在 package.json 的 scripts 属性中加入命令（例如："foo": "echo foo"）就可以通过 npm run foo 运行对应命令。
* 这是 npm 提供的一个很方便的运行项目相关的自动化任务的机制，
---
* [npm WARN checkPermissions Missing write access](https://stackoverflow.com/questions/45106627/npm-checkpermissions-missing-write-access-to-node-modules-is)

#### [npx](https://zhuanlan.zhihu.com/p/27840803)

#### 查看全局安装过的包
```
npm list -g --depth 0
```

#### yarn
1. install
```
yarn add x --dev
```
等价于
```
npm install -D x
```
2. 执行script命令
```
  "scripts": {
    "build":"rm -rf dist;webpack",
  },

yarn build
```
等价于
```
npm run build
```
---
---
#### [安装依赖，yarn.lock和package.json都要有](https://yarnpkg.com/lang/en/docs/cli/install/)

#### 安装并使用 http-server
* 安装
```
npm install -D http-server
```
* 使用
```
// 在 index.html 目录下执行 
http-server . -c-1 
```
 
#### 不要 npm init -y 之后 yarn add
> 直接执行下面命令
```
yarn add webpack-dev-server -D
```

#### 更新依赖
1. 删除 node_modules
```
rm -rf node_modules
```
2. 删除 yarn.lock
```
rm -rf yarn.lock
```
3. 安装依赖
```
yarn install
```
#### yarn 的安装
应该通过 yarn.msi 而非 npm 安装

#### 将 Babel 回退为指定版本
1. 修改 package.json
```
typeScript:^5.8.38
```
2. 安装依赖
```
yarn install
```
3. 然后你可以执行 npm ls babel 来查看本地项目的 babel 版本


