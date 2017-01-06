# 婚礼请柬

**请注意：本系统仅测试了在主流手机微信平台上的兼容性。**

**请注意：PC没有做兼容，所以PC打开会很乱。**

**请注意：请在微信坏境打开，其他任何浏览器均没有测试。**

> 本系统设计灵感与部分图片来源于[微请柬](http://www.wqingjian.com/)

> 如有侵权，请联系本人删除。

## 技术栈

* React

* Webpack

* Redux

* ES6

* Css3

* PHP

## 主要文件夹说明

1. 核心代码放心`src`目录下。

2. 公共资源放在`src/asset`下。

## 后端代码说明
1. 后端代码在根目录`php`文件夹下,需要的`sql`文件放在该目录下。

2. 后端是用PHP写的，主要实现了简单的祝福语插入与查询接口。

3. 相应的接口端口配置在`server.js`下。代理`/wedding`开头的路径到80服务器（后端项目端口）。

    ```
    app.use(proxy('/wedding', {
        target: 'http://localhost:80',
        changeOrigin: true
    }));
    ```

## 开发坏境启动

1. `npm install`

2. `npm start`

3. 浏览器访问 [http://localhost:8081](http://localhost:8081)


## 生产坏境打包

1. `npm run bundle`

##其他说明

1. 系统分男方版本和女方版本，如果访问首页带参数`?t=girl`，则为访问女方版本，否则访问男方版本。
   
    具体版本区别请看代码。下面举一个例子：
    
    ```
    <audio className="hidden" id="talk-audio">
    <source src={userType == 'boy' ? boyMp3 : girlMp3} type="audio/mpeg"/>
    </audio>
    ```
    
2. 所有可配置的照片放在`src/asset/images/photos`，所有可配置的音频放在`src/asset/audio`。