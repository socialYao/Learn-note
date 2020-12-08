# 微信小程序引入vant ui组件的步骤

## 1、在小程序项目根目录上初始化npm

```
npm init
```



## 2、执行命令

```
npm install --production
```



## 3、启用npm

打开   工具-》构建npm，打开   详情-》使用npm模块



## 4、执行VantUI提供的安装命令

```
npm i @vant-weapp -S --production
```

VantUI官网： https://vant-contrib.gitee.io/vant-weapp/#/quickstart

成功之后显示，并且可以看到多了一个：miniprogram_npm 目录



## 5、修改文件

1、修改app.js

将 app.json 中的 `"style": "v2"` 去除，小程序的[新版基础组件](https://developers.weixin.qq.com/miniprogram/dev/reference/configuration/app.html#style)强行加上了许多样式，难以覆盖，不关闭将造成部分组件样式混乱。

2、修改 project.config.json

开发者工具创建的项目，`miniprogramRoot` 默认为 `miniprogram`，`package.json` 在其外部，npm 构建无法正常工作。

需要手动在 `project.config.json` 内添加如下配置，使开发者工具可以正确索引到 npm 依赖的位置。

```json
{
  ...
  "setting": {
    ...
    "packNpmManually": true,
    "packNpmRelationList": [
      {
        "packageJsonPath": "./package.json",
        "miniprogramNpmDistDir": "./miniprogram/"
      }
    ]
  }
}
```



## 5、引入组件

只需要在`app.json`中配置 组件 对应的路径即可。比如Button

```
"usingComponents": {
  "van-button": "miniprogram_npm/vant-weapp/button/index"
}
```

## 6、使用组件

在需要使用组件的页面

```
<van-button type="primary">按钮</van-button>
```

