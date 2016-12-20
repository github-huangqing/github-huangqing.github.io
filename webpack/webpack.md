
# Webpack 简明使用教程


## 使用webpak

[webpak官网教程](http://webpack.github.io/docs/tutorials/getting-started/)  
[The Front-end Tooling Book](http://tooling.github.io/book-of-modern-frontend-tooling/dependency-management/webpack/getting-started.html)

通过 npm init 创建 package.json
~~~~
npm init 
~~~~

安装全局webpake
~~~~
$ npm install webpack -g
~~~~


保存至项目文件夹饼写入配置文件
~~~~
$ npm install webpack --save-dev
~~~~

手动合并文件命令
~~~~
$ webpack ./entry.js bundle.js
~~~~

加载css、style解析模块
~~~~
$ cnpm install style-loader --save-dev
$ cnpm install css-loader --save-dev
~~~~


## 安装运行 webpack-dev-server

浏览器打开 http://localhost:8080/ 或 http://localhost:8080/webpack-dev-server/

安装
~~~~
$ npm install webpack-dev-server -g
$ npm install webpack-dev-server --save-dev
~~~~

执行服务
~~~~
$ webpack-dev-server --progress --colors
~~~~

执行服务:指定执行目录
~~~~
$ webpack-dev-server --content-base dist/
~~~~

