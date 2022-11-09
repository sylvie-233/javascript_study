# Rest Client 插件

Sylvie233的Rest Client插件学习~~~

> Author: Sylvie233
>
> Date: 2022/11/9

[TOC]

## 介绍

api请求测试插件



## 基础使用

文件后缀：`.http`或`.rest`

基础使用

```
POST  http://localhost:3002/getLog
Content-Type: application/json

{
    "mongoUrl": "mongodb://49.232.9.254:27017",
    "collection": "main",
    "num": 10
}
```



注释：#



请求分隔：###



post请求发送的数据为json格式



鼠标放在编写的HTTP请求，右键选择Generate Code Snippet，选择需要生成的语言，可生成对应语言的该请求代码片段



变量

通过@定义变量，{{}}使用变量

```
@name = "Sylvie233"

GET {{name}}/xxx
```



可根据切换环境定义变量



