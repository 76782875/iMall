# iMall
基于Laravel5.2，Vue.js1.0的微信商城

[iMall Backend](http://imall.lovchun.com "iMall 后台管理首页")

[iMall Fronted](http://imall.lovchun.com/mall "iMall 微信商城首页")

[Laravel Vue Blog](https://git.oschina.net/nir_passion/LVBlog "基于Laravel Vue的个人博客")

微信接口测试公众号

![iMall Qrcode](http://oewvb9bk1.bkt.clouddn.com/iMall.jpg "iMall Qrcode")

**可以直接注册一个账号进行浏览**

**不需要配置公众号信息，此功能将移除，替换为配置文件**

**iMall 功能陆续开发中，浏览后台请勿删除任何数据**

:wink: :kissing_heart: :yum: :joy:

## 环境要求
1. PHP≥5.59
2. composer:1.2.1
3. node:v6.2.0
4. npm:3.8.9

## PHP 扩展
1. open_ssl
2. fileinfo

## TODOS
1. 对接微信支付
2. CMS订单管理模块
3. CMS UI 替换为Inspinia

## Composer 、NPM配置
``` shell
#启动composer中国镜像服务
composer config -g repo.packagist composer https://packagist.phpcomposer.com
#启动npm淘宝源
npm config set registry https://registry.npm.taobao.org
#如果上一步配置正确这个命令会有字符串response
npm info underscore
#接下来，设置node-sass
npm config set sass_binary_site https://npm.taobao.org/mirrors/node-sass/
```

## 安装步骤
### 安装Composer Package
``` shell
git clone https://github.com/PassionZale/iMall.git
cd iMall/
git update-index --assume-unchanged config/wechat.php
cp .env.example .env
#在.env中配置好数据库连接后，继续执行以下步骤
composer update
php artisan key:generate
php artisan migrate
```

### 安装NPM Package
``` shell
cd iMall/
npm install
#若出现以下，且NPM未报错
> node-sass@3.11.2 install /usr/share/nginx/html/iMall/node_modules/node-sass
> node scripts/install.js
#执行以下命令
npm install npm install node-sass@3.11.2 /usr/share/nginx/html/iMall/node_modules/node-sass
#编译sass
gulp admin-sass
gulp mall-sass
```

## 组件开发
开发阶段，我们需要实时编译*.vue，*.sass等文件，想要npm执行多个进程，可以使用concurrently这个工具
``` shell
npm install -g concurrently
concurrently "npm run taskA" "npm run taskB"
```
拿本项目来说，可以这样：
``` shell
concurrently "webpack --watch" "gulp watchsass"
```

>人生不是接力跑，是马拉松，努力会有回报

>加油，年轻没有失败
