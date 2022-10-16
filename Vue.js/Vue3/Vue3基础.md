# Vue3基础

Sylvie233的Vue3学习~~~

> Author: Sylvie233
>
> Date: 2022/10/16



>Upate: 22/10/16
>
>Point: 小满Vue(P14)



[TOC]

## Vue3介绍

MVVM架构

Compositon API区分于Vue2的Option API

setup简单\<script>（只能有一个，\<script>标签可以有多个）

vscode插件：volar（禁用Vue2插件：vetur）

虚拟DOM、Diff算法





### 新建项目

Vite构建

`npm init vite@latest`

选择Vue+Typescript

项目依赖

1. vue

2. @vitejs/plugin-vue

3. typescript

4. vite
5. vue-tsc



Vue脚手架构建

`npm init vue@latest`

项目依赖

1. vue
2. @types/node
3. @vitejs/plugin-vue
4. @vue/tsconfig
5. npm-run-all
6. typescript
7. vite
8. vue-tsc



### 目录结构

1. /public
2. /src
   1. /assets
   2. /components
   3. App.vue
   4. main.ts
   5. style.css
   6. vite-env.d.ts
3. index.html
4. package.json
5. tsconfig.json
6. vite.config.json



## Vue3基础语法

### 模板语法

```vue
<template>
	{{msg}}
</template>


```



### 常用指令

#### 1.v-text

#### 2.v-html

#### 3.v-if/v-else-if/v-else

#### 4.v-show

#### 5.v-on/@

常用修饰符：

- stop
- prevent
- once

#### 6.v-bind/:

#### 7.v-model

#### 8.v-for

:key绑定

```
v-for="(item,index) in items"


```



### 生命周期

1. onBeforeMount/onMounted
2. onBeforeUpdate/onUpdated
3. onBeforeUnmount/onUnmounted
4. onRenderTracked







## Vue3常用API

### 1.DefineComponent

DefineComponent<Props,RawBindings>



### 2.ref/Ref/isRef/shallowRef/triggerRef/

模板中不用.value

```
const key:Ref<T> = ref<T>(value)
key.value.xxx

```

模板中使用ref属性：引用真实dom

```
<div ref="xxx"></div>

const xxx = ref()
xxx.value
```



shallowRef浅层次响应式（ref与shallowRef不要写在一块）

triggerRef():强制触发ref更新

customRef()：自定义Ref

```js
function myRef<T>(value: T) {
    return customRef((track, trigger) => {
        return {
            get () {
                track()
                return value
            },
            set (newValue) {
                value = newValue
                trigger()
            }
        }
    })
}
```



### 3.reactive/readonly/shallowReactive/

reactive()：接收引用类型（Array，Object，Map，Set）

不用写.value

```
const xxx = reactive<T>({})
```



### 4.toRef/toRefs/toRaw/

常配合解构语法使用：取出其中的响应式属性

```
const xxx = toRef(obj, key) // obj必须为响应式对象

const { x, y } = toRefs(obj)
```

toRew()：解除响应式（Proxy）



### 5.computed

计算属性

```
const xxx = computed<T>(() => {
	return value
})

const xxx = computed({
	get () {
	
	},
	set (val) {
		
	}
})
```



### 6.watch/watchEffect

```
watch(src, (newVal, oldVal) => {

}, {
	deep: true, // 默认无法侦听到深处
	immediate: true
})
// src可为数组Array
// src为函数，侦听对象中的指定属性


const stop = watchEffect((oninvalidate) => {
	oninvalidate(() => {}) // 操作之前执行的操作
}, {
	flush: "post"/"pre",
	onTrigger(e) {},
})
stop() // 停止监听
```



### 7.onBeforeMount/onMounted/onBeforeUpdate/onUpdated/onBeforeUnmount/onUnmounted/



### 8.onRenderTracked/



### 9.getCurrentInstance





## 第三方库集成











