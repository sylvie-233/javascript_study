# Pinia基础

Sylvie233的Pinia学习~~~

> Author: Sylvie233
>
> Date: 2022/10/16

[TOC]

## Pinia介绍

取代Vuex

安装依赖

`npm i pinia -S`

基础使用

```
// store.ts
import { defineStore } from "pinia"

export default defineStore("name", {
	state: () => {
		return {}
	},
	getters: {
	
	},
	actions: {
		func() {
			this.xxx
		}
	}
})


// 使用
import useMyStore from "./store"

const store = useMyStore()
store.xxx/xxx()
store.$patch({k: newVal})
store.$patch((state) => {
	state.xxx
})
store.$state
```





## Pinia基础语法

### State



### Actions

可以为异步方法



### Getters













## Pinia常用API

### 1.createPinia



### 2.defineStore



### 3.storeToRefs/



### 4.$state/$patch/$reset/$subscribe/$onAction

```



store.$subscrive((args, state) => {
	
}, {
	detached: true,
	deep: true,
	flush: true
})

store.$onAction((args) => {
	args.after(() => {
		
	})
}, true)
```









## Pinia补充

### Pinia插件

```
const myPlugin = (ctx: PiniaPluginContext) => {
	const {store} = ctx
	
}


store.use(myPlugin)
```



