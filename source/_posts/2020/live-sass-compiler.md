---
title: live-sass-compiler
date: 2020-09-20 19:52:37
tags: ["vscode", "sass"]
category: 前端
---
vscode live-sass-complier插件, 能够实时将sass/scss编译成css

## 打开vscode应用商店，输入Live Sass Complier，搜索并安装
![livesasscomplier](live-sass-complier/live-sass-complier.png)

## 在自己的项目根目录 .vscode/settings.json中添加如下配置信息，也可以添加到vscode的全局配置settings.json中

```json
    {
        "liveServer.settings.port": 5501,
        "liveSassCompile.settings.formats":[
            {
                //css输出模式 expanded展开的多行css代码，compact简洁格式的css代码，
                //           compressed压缩后的css代码，nested嵌套缩进的css代码
                "format": "compress",
                //输出文件拓展名 .css  .min.css  .wxss
                "extensionName": ".css",
                //指定输出目录
                "savePath": "public/css"   
            }
        ],
        //是否生成map文件
        "liveSassCompile.settings.generateMap": true,
        //处理浏览器兼容性样式
        "liveSassCompile.settings.autoprefix": [
            ">1%",
            "last 2 versions"
        ],
        //排除编译某些css
        "liveSassCompile.settings.excludeList": [
            "**/node_modules/**",
            ".vscode/**"
        ]
    }
```

如果没有指定编译文件，会默认编译所有可以编译的sass/scss文件，如果只想单独编译某一个文件，可以在excludeList中设置不编译所有文件夹子。
```json
    {
        "liveSassCompile.settings.excludeList": [
            "**"
        ],
        //指定编译某些文件
        "liveSassCompile.settings.includeItems": [
            "public/css/index.scss"
        ]
    }
```

## 编译（停止编译）文件
> ctrl + shift + p 输入Live Sass: Watch Sass开始进行实时编译，
>                  输入Live Sass: Stop Watching Sass停止实时编译，
>                  输入Live Sass: Compile Sass - Without Watch Mode进行一次编译
> 或者在vscode底部控制栏点击 watch sass进行编译
