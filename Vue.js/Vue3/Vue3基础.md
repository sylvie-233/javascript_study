# Vue3基础

> Author: Sylvie233
>
> Date: 22/10/16
>
> Point:  
> 	尚硅谷Vue3入门到实战，最新版vue3+TypeScript前端开发教程：P22



[TOC]

## 基础介绍

MVVM架构

Compositon API区分于Vue2的Option API

setup简单\<script>（只能有一个，\<script>标签可以有多个）

vscode插件：volar（禁用Vue2插件：vetur）

虚拟DOM、Diff算法

三种创建组件的方法：

1. 原版vue
2. jsx/tsx
3. h函数

Vue宏："vue/macros"

















### 项目目录

```
vue-cli脚手架:
	/node_modules:
	/public:
		favicon.ico:
		index.html:
	/src:
		/assets:
		/components:
		/router:
		/views:
		App.vue:
		main.ts:
		env.d.ts:
	.gitignore:
	babel.config.js:
	package.json:
	tsconfig.json:
	vue.config.js:
```



`vue.config.js`

```
const { defineConfig } = require("@vue/cli-service")

module.exports = defineConfig({
	transpileDependencies: true,
	configureWebpack: {
		plugins: []
	}
})
```



`package.json`

```
{
	"eslintConfig": {
		"rules": {
			
		}
	},
}
```





`tsconfig.json`

```
{
	"compilerOptions": {
		"target": "exnext",
		"baseUrl": ".",
		"types": [
			"webpack-env"
		],
		"paths": {
			"@/*": ["src/*"]
		},
		"lib": ["esnext",],
	},
	"include": [],
	"exclude": []
}
```



`env.d.ts`：.vue文件的声明

```
declare module "*.vue" {
	import type { DefineComponent } from "vue"
	const component: DefineComponent<{}, {}, any>
	export default component
}
```













































### vue

```
vue:
	create:
```



### vue-cli-service

```
vue-cli-service:
	serve:
```





### vue-tsc

```
vue-tsc:
	--noEmit:
```





## 核心内容

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

props+emit

modelValue+emit("update:modelValue", val)

绑定自定义组件

```
defineProps<{
	modelValue: T,
	xxxModifiers: {
		xxx?: xxx
	}
}>()
```

自定义修饰符

xxxModifiers



#### 8.v-for

:key绑定

```
v-for="(item,index) in items"


```

#### 9.v-slot/#  





### 生命周期

1. onBeforeMount/onMounted
2. onBeforeUpdate/onUpdated
3. onBeforeUnmount/onUnmounted
4. onRenderTracked
5. onActivated/ondeactivated



### 组件传值

props传递  

```
defineProps<T>({

})
```

事件传递

```
const emit = defineEmits(['on-click'])
emit('on-click')
```

provider传递

```
provide(k, val)
inject<T>(k)
```







### 组件注册

全局注册

```
createApp(App).component(Xxx)
```

局部注册

setup中import引入即可 



### slot插槽

```
<slot></slot>

<slot name="" :data></slot>

v-slot:name="{data}"

#[valName] // 动态插入
```



### Css扩展

样式穿透：:deep()

插槽选择：:slotted()

全局选择：:global()

动态css：css中可使用v-bind()

CssModule:

```
<style module=""></style>

$style.xxx

const xxx = useCssModule("")
xxx.xxx
```







### 内置组件

#### 1.\<component>

动态组件

```
<component :is=""></component>
```



#### 2.\<Suspense>

异步加载组件

```
<Suspense>
	<template #defalut/>
	<template #fallback/>
</Suspense>
```



#### 3.\<Teleport>

```
<Teleport to="" :disabled=""></Teleport>
```



#### 4.\<keep-alive>

```>
<keep-alive :include="[]" :exclude="[]" max=""></keep-alive>
```



#### 5.\<transition>

```
<transition 
	name=""
	enter-from-class=""
	leave-from-class=""
	duration=""
	@before-enter
	@enter
	@after-enter
	@enter-cancelled
	@before-leave
	@leave
	@after-leave
	@leave-cancelled
	appear
	appear-from-class
	appear-active-class
	appear-to-class
	></transition>
	
const enterFrom = (el: Element, done: Function) => {}
```

css类名：

1. -enter-from/-enter-active/-enter-to
2. -leave-from/-leave-active/-leave-to



\<transition-group>:列表过渡

```
<transition-group
	tag=""
	move-class=""
	其余属性与transition一样
>
</transition-group>
```



### 自定义属性

```
app.config.glabalProperties.$xxx = xxx
declare module "vue" {
	export interface ComponentCustomProperties {
		$xxx: typeof Xxx
	}
}

const instance = getCurrentInstance()
instance.proxy.$xxx

declaremodule "@vue/runtime-core" {}

```



### 自定义指令

钩子函数

1. created
2. beforeMount
3. mounted
4. beforeUpdate
5. update
6. beforeUnmount
7. unmounted

Directive

```
(el: HTMLElement, binding: DirectiveBinding,) => {

}

interface DirectiveBinding<V> {
	instance: ComponentPublicInstance | null
	value: V
	oldValue: V | null
	arg?: string
	modifiers: DirectiveModifiers
	dir: ObjectDirective<any, V>
}

// 简写方式
const vXxx: Directive<any, void> = (el: HTMLElement, binding: DirectiveBinding<T>) => {

}
v-xxx
```



### 自定义插件

```
import type {App} from "vue"
export defautl {
	install(app: App) {
	
	}
}

app.use(Xxx)
```







## 常用API

```
vue:
	createApp():
		mount(): 挂载
		use(): 使用插件
	computed():
	defineComponent():
		components:
		name:
		render():
		setup():
	defineProps():
	onMounted():
	ref():
	reactive():
	toRefs():
	watch():
	
	
	
vue-router:
	Router:
	RouteRecordRaw:
	createRouter():
		addRoute():
		afterEach():
		beforeEach(): 全局前置守卫
	createWebHistory():
	useRoute():
		---
		hash:
		params:
		name:
		path:
		matched:
		query:
		redirectedFrom:
	useRouter():
		---
		getRoutes():
		push():
			name:
			path:
			params: {}
			query: {}

vuex:
	createStore():
	useStore():
		commit():
		dispatch():
		
	
element-plus:
	FormInstance:
		---
		validate():
			isValid:

axios:
	create():
		baseURL:
		timeout:
		headers: {}
		---
		interceptors:
			request:
				use():
					(config) => config
			response:
				use():
					(resp) => resp:
		():
			url:
			method:
			data:
		get():
		post():
```



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



### 4.toRef/toRefs/toRaw/markRaw/

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



### 10.defineProps/withDefaults/



### 11.defineEmits



### 12.defineExpose



### 13.defineAsyncComponent

```
const Xxx = defineAsyncComponent(() => import())
```



### 14.provide/inject



### 15.useAttrs/useSlots/useCssModule/



### 16.App/VNode/



### 17.createVNode/render/h/



### 18.nextTick/



### 19.defineCustomElement







## 第三方库

### VueRouter

安装

```
npm install vue-router@4 -S
```



目录结构

```
:
	/router:
		index.ts
```



`router/index.ts`

```
const routes: Array<RouteRecordRaw> = [
	{
		path: "/",
		name: "xxx",
		meta: {},
		component: () => import("xxx.vue"),
		children: []
	},
]

const router = createRouter({
	history: createWebHistory(),
	routes,
	scrollBehavior: (to, from, savePosition) => {
		return {
			top,
		}
	}
})

export default router
```



常用组件

```
:
	<router-view>:
```





### Vuex

安装

```

```



目录结构

```
:
	/store:
		index.js:
```



`store/index.js`

```
import { createStore } from "vuex"

export default createStore({
	state: {},
	getters: {},
	mutations: {},
	actions: {},
	modules: {},
})
```







### Pinia



### ElementPlus

安装

```
npm install element-plus -S
```



基础使用

```
import ElementPlus from "element-plus"
import "element-plus/dist/index.css"

app.use(ElementPlus)
```



常用组件

```
:
	<el-button>:
	<el-form>:
		<el-form-item>:
```







### 集成Less

安装依赖：

`npm i less less-loader -D`

直接使用：

```
<style lang="less"></less>
```





### 集成Animate.css



### 集成Mitt

发布订阅模式EventBus



### 集成Jsx



### 集成TailwindCss

安装依赖：

`npm i -D tailwindcss@latest postcss@latest autoprefixer@latest`

生成tailwindcss配置文件:

`npx tailwindcss init -y`



### 集成UnoCss

unocss：css原子化



### 集成Echarts





## 项目构建

### Webpack构建

配置文件：

- webpack.config.js

安装依赖

`npm i webpack webpack-cli webpack-dev-server -D`

`npm i vue-loader@next @vue/compiler-sfc -D`

`npm i css-loader style-loader -D`

`npm i typescript ts-loader -D`





## 知识点补充

### 环境变量

.env文件

- .env
- .env.development
- .env.production

```
import.meta.env
process.env

vite --mode development/production/
```



### 性能优化

Lighthouse报告

rollup打包分析

vite的build优化



### Web Components

#shadow-root隔离

```
class Xxx extents HTMLElement {
	constructor() {
		super()
		const dom  this.attachShadow({
			mode: "open"
		})
		dom.appendChild(document.createElement(xxx))
	}
	connectedCallback() {}
	disconnectedCallback() {}
	adoptedCallback() {}
	attributeChangedCallback() {}
}

window.customElements.define("name", Xxx)
```



Vue集成Web Components





