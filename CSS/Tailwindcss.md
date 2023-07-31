# Tailwindcss基础

> Author: Sylvie233
>
> Date: 23/03/11
>
> Point: 

[TOC]

## 基础介绍

安装

```
npm install tailwindcss postcss autoprefixer
```





### tailwind.config.js

```
module.exports = {
	purge: [
		"./index.html",
	],
	darkMode: false,
	theme: {
		extend: {},	
	},
	variants: {
		extend: {},
	},
	plugins: [],
}
```



### tailwindcss

```
tailwindcss:
	init:
		-p:
```



### tailwindcss-cli

```
tailwindcss-cli:
	build: // 编译生成tailwind.css文件
		-o: 
```



### tailwind.css

```

```





## 核心内容

```
tailwind:
	absolute:
	bg-gray-900:
	block:
	border:
	border-b:
	border-gray-600:
	cursor-pointer:
	divide-y:
	divide-gray-300:
	fill-current:
	flex:
	flex-col:
	flex-row:
	flex-wrap:
	font-semibold:
	group:
	group-hover::
	h-3:
	h-full:
	hidden:
	hover::
	items-center:
	justify-between:
	lg::
	max-w-sm:
	ml-2:
	mr-2:
	mx-1:
	placeholder-gray-400:
	px-4:
	py-3:
	relative:
	right-0:
	rounded:
	rounded-full:
	rounded-xl:
	rounded-r-none:
	shadow:
	shadow-sm:
	space-x-4:
	-space-x-2:
	text-gray-900:
	text-right:	
	text-sm:
	text-white:
	top-0:
	truncate:
	underline:
	w-6:
	w-3/4:
	w-full:
```



### 指令

`style.css`：脚手架项目中导入该css文件即可使用tailwindcss

```
@tailwind base;
@tailwind components;
@tailwind utilties;
```

































