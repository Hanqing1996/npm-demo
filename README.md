# npm笔记

#### 其它
* 永远别用cnpm!!!!
* 配置淘宝npm镜像
```
npm config set registry https://registry.npm.taobao.org
```
* 如果一个包是给用户（用这个组件的程序员）使用的
```
npm i vue
```
* 如果一个包是给开发者使用的（-D表示给 developer 使用）,比如 chai
```
npm i -D parcel-bundler
```  

#### npm root -g
显示全局安装的包的路径

#### npm install
* 按照package.json初始化项目
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

* npm run
    * 在 package.json 的 scripts 属性中加入命令（例如："foo": "echo foo"）就可以通过 npm run foo 运行对应命令。
    * 这是 npm 提供的一个很方便的运行项目相关的自动化任务的机制，