# Uniapp基础

> Author: Sylvie233
>
> Date: 23/03/12
>
> Point: P42

[TOC]

## 基础介绍



rpx响应式单位：750rpx











































vue2目录结构

```
vue2:
	/components:
		/xxx:
			xxx.vue:
	/pages:
		/index:
			index.vue:
	/static:
		logo.png:
	/unpackage:
	App.vue:
	index.html:
	main.js:
	manifest.json:
	pages.son:
	uni.scss:
```



`manifest.json`

```
{
	
}
```



`pages.json`

```
{
	"pages": [ // 路由页面注册
		{
			"path": "pages/index/index",
            "style": {
            	"enablePullDownRefresh": false,
            	"navigationBarBackgroundColor": "#ffffff",
            	"navigationBarTextStyle": "white",
            	"navigationBarTitleText": "uni-app",
            },
		},
	],
	"tabBar": { // 底部tabBar
		"color": "#fffff",
		"selectedColor": "#fffff",
		"iconfongSrc": "static/fonts/xxx"
		"list": [
			{
				"text": "首页",
                "pagePath": "page/index/index",
                "iconfont": {
                	"text": "\uxxxx",
                	"selectedText": "\uxxxx",
                	"color": "#fff",
                	"selectedColor": "#xxx",
                },
                "iconPath": "/xxx",
                "selectedIconPath": "/xxx",
			},
		],
	},
	"globalStyle": {
        "backgroundColor": "#F8F8F8",
        "navigationBarBackgroundColor": "#F8F8F8",
		"navigationBarTextStyle": "black",
		"navigationBarTitleText": "uni-app",
		
		
	},
	"uniIdRouter": {},
}
```



`main.js`

```
import Vue from "vue"
import App from "./App"

Vue.config.productionTip = false
App.mpType = "app"
const app = new Vue({
	...App
})

app.$mount()
```









## 核心内容

```
uni:
	hideLoading():
	hideTabBar():
		animation:
	hideToast():
	navagateBack():
	navigateTo():
		url:
		success(res):
	redirectTo():
	reLaunch():
	removeTabBarBadge():
		index:
	request():
		url:
		data:
		method:
		header: {}
		timeout:
		success():
			res:
				data:
		---
	setNavigationBarColor():
		frontColor:
		animation: {}
    setNavigationBarLoading():
	setNavigationBarTitle():
		title:
	setTabBarBadge():
		index:
		text:
	setTabBarItem():
		index:
		text:
		pagePath:
		visible:
		iconfont: {}
	setTabBarStyle():
		color:
		selectedColor:
	showActionSheet():
		title:
		itemList:
		success(res):
	showLoading():
		title:
	showModal():
		title:
		content:
		showCancel:
		cancelColor:
		cancelText:
		editable:
		placeholderText:
		success():
			confirm:
			errMsg:
		fail():
		complete():
	showTabBarRedDot():
	showToast():
		title:
		duration:
		icon:
		image:
		mask: true
		complete():
		success():
		fail():
    switchTab():
```





### Vue2

```
vue:
	Vue:
		config:
			devtools:
			errorHandler:
			optionMergeStrategies:
			silent: 取消日志
			warnHandler:
		component():
		nextTick():
		set():
		use():
		
		
		
Component:
	name:
	props: []|{}
	components: {}
	data():
	methods: {}
	computed: {}
	
	beforeCreate():
	created():
	beforeMount():
	mounted():
	beforeUpdate():
	updated():
	activated():
	deactivated():
	beforeDestroy():
	destroyed():
	errorCaptured():
	
	
	onLaunch():
	onShow():
	onLoad():
		params:
	onHide():
	---
	$route:
		fullPath:
		hash:
		matched:
		meta:
		name:
		params:
		path:
		query:
		type:
	$emit():
	


指令:
	v-if/v-else/v-else-if:
	v-show:
	v-for:
	v-bind/::
		.sync: 子传父props(update:xxx事件)
	v-on/@:
		.native: 原生事件
	v-html/v-text:
	v-once:
	v-model:
```









### 内置组件

```
uni组件:
	<audio>:
	<button>:
	<checkbox>:
	<editor>:
	<form>:
	<icon>:
	<image>:
		lazy-load:
        mode:
        	scaleToFill:
		src:
	<input>:
	<label>:
	<navigator>:
		open-type:
			redirect:
		url:
	<picker>:
	<picker-view>:
	<progress>:
	<radio-group>:
        <radio>:
	<rich-text>:
	<scroll-view>:
		scroll-x: true|
		scroll-y:
	<slide>:
	<swiper>:
		autoplay:
		duration:
		circular:
		interval:
		loop: true|
		<swiper-item>:
	<switch>:
	<text>:
		decode:
		selectable:
		space:
			ensp:
	<textarea>:
	<video>:
		autoplay:
		controls:
		muted:
		src:
	<view>:
```















## 第三方库

### uView

```
uView:
	
```

























