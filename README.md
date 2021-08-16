# 微前端实战

* [参考资料](https://juejin.cn/post/6875462470593904653)
  
## 构建项目

(最好使用npm构建，否则package.json中要增加start启动命令)  
vue create main  
vue create sub-vue  
npx create-react-app sub-react  
cd main  
yarn add qiankun  
npm install sass-loader --save-dev  

## 基座配置

跟子应用有关的都放在micro-app.js文件中  
保存全局状态，拷贝store.js  
修改App.vue，定义挂载子应用id： subapp-viewport  
新增.env.development和.env.production分别配置端口号  
首次加载子应用比较慢，需要使用进度条功能 npm install --save nprogress  

## vue子应用配置

子应用名称应与micro-app.js中名称保持一致（可以直接使用package.json中的name作为output）  
新增.env配置端口号（与父应用配置一致）  
新增src/public-path.js  
增加路由功能，router目录及view目录    
增加store功能  
改造main.js  
npm install --save common vue-router vuex  

## react子应用配置

新增.env配置端口号  
为了不eject所有webpack配置，我们用react-app-rewired方案复写webpack  
* npm install react-app-rewired --save-dev  
* 新建sub-react/config-overrides.js  
新增src/public-path.js，src/serviceWorker.js    
改造index.js  

## 抽取公共代码

拷贝common  

## 项目统一打包

拷贝sub-html，npm install  
准备package.json  
聚合库安装： npm i npm-run-all -D  

## 解决问题

用到公共库的必须用npm方式安装，不能直接拷过去： npm install file:../common  
react在qiankun下必须用react-app-rewired来启动  
调试时先尝试单独子应用正常，如基座下不正常，则修改micro-app.js排除加载变量的问题  