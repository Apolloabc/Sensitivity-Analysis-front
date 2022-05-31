# Sensitivity-Analysis-front

> 2022.05.21，完善项目基本信息
> 基于Vue2 + ElementUI所搭建的敏感性分析前端项目
> Vscode中需要安装Vuter插件，解析vue2模板。注意Volar插件不可以，它是针对vue3模板的。
>
> 广义的话，SA平台涉及到OpenGMS组内的很多个系统，可以参考论文中4.4.3的分布式运行架构图，相信聪明的你可以看得懂，如果没有的话，努力把它看懂，你就算对咱们组的技术架构完全入门了。
> 狭义的话，SA平台设计到SA前端和SA后端这两个代码系统，以及MongoDB和GeoServer这两个数据存放系统。
>
> 目前部署情况：
> 172.21.212.44: 前端使用Nginx部署, 后端直接运行jar包，两者之间通过Nginx转发请求。
> 172.21.212.43: 放有SWAT服务的模型容器，存放地理数据的GeoServer

> GitHub网址：https://github.com/Apolloabc/Sensitivity-Analysis-front

## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report
```



## 目录结构

> 2022.05.29

```js
|-- SA-PROJECT
	// 以下两个为webpack的配置文件夹
    |-- build
    |-- config
    |   |-- index.js // 在这里配置代理接口和启动端口等信息
    |   |-- **
    // 项目源码位置
    |-- src
    |   |-- App.vue // 根节点
    |   |-- main.js // 入口文件，加载各种公共组件
    |   |-- assets // 资源路径，logo放在这，放在下面的static可能会找不到
    |   |-- components // 公共组件，这里放了页面的首位组件和MapBox组件
    |       |-- Header.vue
    |       |-- Footer.vue
    |       |-- MapBox.vue
    |   |-- router // 前端路由，控制组件的加载
    |   |-- views // 可以结合路由来看
    |       // 1 2 3 资源管理相关的组件
    |       |-- 1 libraryPage // 知识库组件，查看和贡献
    |       |-- 2 managePage // 项目管理组件，项目查看、收敛性、可信度检验
    |       |-- 3 modelList // 模型组件，查看和贡献（TODO）
    |       // 4 5 支持模型单次运算的组件（TODO）
    |       |-- 4 paramCaResult 
    |       |-- 5 paramStateSR
    |       // 6 ~ 13 SA流程相关组件
    |       |-- 6 dataState
    |       |-- 7 paramState
    |       |-- 8 processStep // 模型运行
    |       |-- 9 saPage // SA项目页面 涉及6~13
    |       |-- 10 scoreSA
    |       |-- 11 scoreSAQual // 定性
    |       |-- 12 simResult // 模型模拟结果
    |       |-- 13 simSetting // 模拟配置
    |-- static
    |-- README.md
```

> Tips:
>
> 1. 点击开始运行之后，可以在服务器 D:\saProjectData 查看参数采样情况
> 2. 可以通过模型容器查看任务分发情况（需要等待几分钟）
> 3. 任务一次次运行成功之后，可以在服务器D:\saProjectData，查看结果的提取情况
>
> 中途可能会由于网络等未知原因，导致模拟任务的失败
>
> 1. processStep组件中的invoke方法，将运行失败的任务重新发布
> 2. 需要对比浏览器中打印的序号，与结果汇总文件中的序号，是否一致（可以直接通过行数来确定）
> 3. 如果出现缺失，可以在服务器中运行结果抽取脚本，手动添加（直到汇总结果总数正确时，才会进行后续的目标函数计算、SA计算）

