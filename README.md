#### bash: tsc: command not found
> yarn global add typescript


#### Yarn - There appears to be trouble with your network connection. Retrying
> Deleting the yarn.lock file and rerunning "yarn install" worked for me.

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
#### yarn info babel versions
查看 babel 的版本信息(从旧到新)

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

#### npm install X --save
* 会把X包安装到node_modules目录中
* 若package.json中有相关记录，则按照记录安装对应版本
* 若package.json中没有相关记录，则安装最新版本，并在package.json的dependencies属性下添加X及安装版本
* 【注意】从 npm5 开始，—save变成了默认参数，无论写不写 —save，依赖都会保存在dependencies 里

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

#### npx 有啥用
参考
* [npm 和 npx 有什么区别？ - 天猪的回答 - 知乎](https://www.zhihu.com/question/327989736/answer/706857512)
* [npx 是什么 - 方应杭的文章 - 知乎](https://zhuanlan.zhihu.com/p/27840803)
* [npx 使用教程-阮一峰](https://www.ruanyifeng.com/blog/2019/02/npx.html)

主要作用如下
1. 自动找当前项目中 node_modles 下的依赖，也就是说:
```js
./node_modules/.bin/webpack
```
等价于
```js
npx webpack
```
2. 对于只使用一次的依赖（比如脚手架），我们可以使用 npx
```
npx create-react-app my-react-app
```
上面代码运行时，npx 将create-react-app下载到一个临时目录，使用以后再删除。所以，以后再次执行上面的命令，会重新下载create-react-app。


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
---
#### devDependencies 和 dependencies 的区别
1. devDependencies 是开发环境下的依赖（axios、webpack、babel、eslint、jest 之类的测试库）。dependencies 是产生环境下的依赖（vue、react、jquery）
2. yarn add -D xx 是把 xx 添加到 devDependencies 对象中， yarn add xx 是把 xx 添加到 dependencies 对象中。yarn global add xx 是全局安装（不安装到 node_modles 目录下）
3. 当我们 clone 了某个库（注意不是安装别人发布在 npm/yarn 上的 lib），执行 yarn install 会依据项目的 package.json 安装 devDependencies 和 dependencies 中所描述的全部依赖。而 yarn install --production 只安装 dependencies 所包括的依赖。
---
#### 不是所有人都把 build 后的文件发布到 npm/yarn
> 如果是打包好的 lib,事实上不需要任何 dependices
* [在 npm 上发布源码](https://zhuanlan.zhihu.com/p/54255260)
---
> 发布npm包的话你这个包的devDependencies的依赖在别人安装你模块的时候并不会安装，只会安装dependencies里的依赖
* 比如我发布的在 npm/yarn 上的 lib,它的 package.json是这样的
```
  "dependencies": {
    "core-js": "^3.4.3",
    "vue": "^2.6.11"
  },
  "devDependencies": {
    "@vue/cli-plugin-babel": "^3.0.0",
    "@vue/cli-plugin-unit-mocha": "^3.0.0",
    "@vue/cli-service": "^3.0.0",
    "@vue/component-compiler-utils": "^2.6.0",
    "@vue/test-utils": "^1.0.0-beta.20",
    "babel-plugin-istanbul": "^5.1.4",
    "chai": "^4.2.0",
    "chai-spies": "^1.0.0",
    "cross-env": "^5.2.0",
    "karma": "^3.0.0",
    "karma-chai": "^0.1.0",
    "karma-chai-spies": "^0.1.4",
    "karma-chrome-launcher": "^2.2.0",
    "karma-coverage": "^1.1.2",
    "karma-mocha": "^1.3.0",
    "karma-sinon-chai": "^2.0.2",
    "karma-sourcemap-loader": "^0.3.7",
    "karma-spec-reporter": "^0.0.32",
    "karma-webpack": "^3.0.0",
    "mddir": "^1.1.1",
    "mocha": "^5.2.0",
    "node-sass": "^4.9.0",
    "sass-loader": "^7.0.1",
    "sinon": "^7.3.2",
    "sinon-chai": "^3.3.0",
    "vue-server-renderer": "2.6.11",
    "vue-template-compiler": "^2.6.11",
    "vuepress": "^1.0.0-alpha.17"
  },
```
别人安装我的 lib
```
yarn add -D zhq-vue-wheel
```
或
```
yarn add zhq-vue-wheel
```
检查此时的 node_modules,会发现目录下的文件结构是这样的
```
|-- node_modules
    |-- vue
    |-- core-js
    |-- zhq-vue-wheel
```
也就是说，devDependencies 里的依赖没有被安装！

---
#### npm-scripts

参考[npm scripts 使用指南-阮一峰](http://www.ruanyifeng.com/blog/2016/10/npm_scripts.html)

指的是 package.json 里的 scripts

```json
{
  // ...
  "scripts": {
    "build": "babel src/index.ts"
  }
}
```

每当执行 scripts 里的命令，会将当前目录的`node_modules/.bin`子目录加入`PATH`变量，执行结束后，再将`PATH`变量恢复原样。

所以

```
yarn build
```

等价于在命令行中输入

```
npx babel src/ndex.ts
```

或者

```
node_modules/.bin/babel src/ndex.ts
```

* npx 有时候用起来很慢：当你要找的包不在 node/module 目录下，也没有进行过全局安装，npx 会远程下载，并在命令执行完毕后删除临时目录，这显然适用于一次性的目录。比如 create-react-app 这样的脚手架搭建命令。这种状态下的稍慢是可以容忍的。但是要注意已在本项目 node/modules 目录下或全局安装的包，npx 不会删除（否则也太 nc 了）
* 对于那些常见的命令，我们在开发时更推荐写入 scripts 里。


