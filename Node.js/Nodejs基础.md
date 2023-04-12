# Nodejs基础

Sylvie233的Vue3学习~~~

> Author: Sylvie233
>
> Date: 2022/10/16

[TOC]

## 介绍

libuv+v8+



### npm

```
npm:
	audit:
	login:
	outdated:
		-l:
	postinstall:
	publish:
		(prepublishOnly|prepack|prepare|postpack|publish|postpublish)
	run:
	version:
		major:
		minor:
		patch:
```



### pnpm

```
pnpm:
	add:
	create:
		vite:
```



#### monorepo

前端多项目工程化管理





`pnpm-workspace.yaml`：定义工作空间

```
packages:
	- "packages/*"
	- "components/**"
	- "api/**"
	- "utils/**"
```



`package.json`：引入其他项目

```
{
	"dependencies": {
		"xxx": "workspace:../../xxx"
	}
}
```





## 核心内容





