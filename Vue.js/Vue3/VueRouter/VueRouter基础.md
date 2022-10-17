# VueRouter基础

Sylvie233的VueRouter学习~~~

> Author: Sylvie233
>
> Date: 2022/10/17

[TOC]

## VueRouter介绍

Vue3使用4版本的Router



安装依赖：

`npm i vue-router@4 -S`



基础使用：

```
import { createRouter, createWebHistory, RouteRecordRaw } from "vue-router"

const routes: RouteRecordRaw[] = [
	{
		path: "/xxx",
		name: "",
		component: () => import("xxx"),
		components: {
			default: () => import("")
		},
		redirect: "",
		redirect: (to) => {
			return {
				path: "",
				query,
			}
		},
		alias: [],
		children: [
			{
				path: "/xxx",
				component,
			},
		],
		meta: {},
	},
]

const router = createRouter({
	history: createWebHistory(),
	routes,
	scrollBehavior: (to, from, savePosition) => {
		return {
			top,
			
		}
	},
})

export default router


app.use(router)


const router = useRouter()
router.push({
	path: "url",
	
})
```





## VueRouter基础语法

### 内置组件

#### 1.\<router-view>

```
<router-view
	name
	#defaul="{route, Component}"
	
></router-view>
```



#### 2.\<router-link>

```
<router-link
	:to="{name: 'xxx', }"
	replace
	
></router-link>
```



### 默认路由



### 路由传参

route

```
const route = useRoute


```



动态路由

```
{
	path: '/xxx/:yyy'
}

route.params.yyy
```



### 嵌套路由

组件的\<router-view>嵌套

```

```



### 命名视图



```

```



### 导航守卫

#### 1.beforeEach

#### 2.afterEach



### 路由元信息



```

```



### 动态路由

routes信息由后端返回

```
router.addRoute({
	path,
	name,
	component: () => import("后台返回路径")
})
```







## VueRouter常用API

### 1.createRouter



### 2.createWebHistory/



### 3.RouteRecordRaw/



### 4.useRouter/useRoute

```
const router = useRouter()

const route = useRoute
```



### 5.push/replace/go/

```
const router = useRouter()

router.push({
	path: "",
	query: {},
	params: {},
})
```





### 6.beforeEach/afterEach/

```
router.beforeEach((to, from, next) => {
	next()
})


```



### 7.addRoute





