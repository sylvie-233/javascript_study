# Vue2基础

> Author: Sylvie233
>
> Date: 23/03/11
>
> Point: 

[TOC]

## 基础介绍



## 核心内容

### 组件

```
Component:
	data():
	methods():

```





### 指令

```
vue内置指令:
	
```











## 第三方库

```
vue:
	Vue:
		el:


pinia:
	PiniaVuePlugin:
	createPinia():
```



### Pinia

安装

```

```



项目目录

```
:
	/stores:
		index.ts:
```



`stores/index.ts`

```
import { defineStore } from "pinia"

export const useMyStore = defineStore({
	id: "xxx",
	state: () => ({}),
	getters: {
		xxxGet: (state) = > state.xxx,
	},
	actions: {
		xxxAct() {
			this.xxx+++
		},
	},
})
```



基础使用

```
import { useMyStore } from "@/stores"

const store = useMyStore()
store.xxxAct():
```













