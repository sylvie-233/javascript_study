# React.js基础

> Author: Sylvie233
>
> Date: 2022/10/21
>
> Point: P153

[TOC]

## 基础介绍



项目依赖

```
:
	react:
	react-dom:
	react-scripts:
```





### 目录结构

```
react项目:
	/node_modules:
	/public:
	/src:
		App.css:
		App.test.tsx:
		App.tsx:
		index.css:
		index.tsx:
		logo.svg:
		env.d.ts:
		reportWebVitals.ts:
		setupTests.ts:
	.gitignore:
	package.json:
	tsconfig.json:
	yarn.lock:
```











### create-react-app

```
create-react-app:
	--template:
		typescript:
```



### react-scripts

```
react-scripts:
	build:
	eject:
	start:
	test:
```





## 核心内容



















## 常用API

```
react:
	React:
		FC:
		StrictMode:
		Suspense:
	lazy():
	useEffect():
	useState():

react-dom:
	/client:
		ReactDOM:
			createRoot():
				render():
	

react-router-dom:
	BrowserRouter:
	Link:
	Navigate:
		to:
	Outlet:
	Route:
		path:
		element:
	Routes:
    useRoutes():
    
redux:
	applyMiddleware():
	combineReducers():
	legacy_createStore():
	
react-redux:
	Provider:
		store:
	useDispatch():
	useSelector():
	
redux-thunk:
	ThunkAction:
	
redux-devtools-extension:
	composeWithDevTools():
	
antd:
	Button:
```





## 第三方库

### ReactRouter

安装

```
npm install react-router-dom
```



目录结构

```
:
	/router:
		index.tsx
```



`router/index.tsx`

```
编程式导航:
	import { BrowserRouter, Routes, Route } from "react-rotuer-dom"
	const router = () => (
		<BrowserRouter>
			<Routes>
				<Route path="/" elment={<Home />}>
					<Route path="/xxx" element={<Xxx />}></Route>
				</Route>
			</Routes>
		</BrowserRouter>
	)
	export default router
	
	import Router from "./router"
	(
		<Router>
			<App />
		</Router>
	)

声明式导航:
	const routes = [
		{
			path: "",
			elememnt: <Xxx />,
		},
	]
	export default routes
	
	(
		<BrowserRouter>
			<App />
		</BrowserRouter>
	)
```



基础使用

```
编程式组件引入:
	import { Outlet, Link } from "react-rotuer-dom"
	
	(
		<Link to="/xxx">xxx</Link>
		<Outlet />
	)

声明式组件引入:
	import {useRoutes, Link} from "react-router-dom"
	import router from "./router"
	const outlet = useRoutes(router)
	(
		<Link to="/xxx">xxx</Link>
		{outlet}
	)
```



懒加载组件

```
import { lazy } from "react"

const Xxx = lazy(() => import("./views/Xxx"))

{
	element: (
		<React.Suspense fallback={<div>}>
			<Xxx />
		</React.Suspense>
	)
}
```





### Redux

安装

```
npm i redux react-redux redux-chunk redux-devtools-extension
```



目录结构

```
:
    /store:
    	/actions:
    		index.ts:
        /reducers:
            index.ts:
        index.ts:
```



`store/index.ts`

```
import { legacy_createStore as createStore, applyMiddleware } from "redux"
import thunk from "redux-thunk"
import { composeWithDevTools } from "redux-devtools-extension"

import reducer from "./reducers"

export default createStore(reducer, composeWithDevTools(applyMiddleware(thunk.withExtraArgument(xxx))))
```



`store/reducers/index.ts`

```
import { combineReducers } from "redux"

function myState(state = {}, action) {
	根据action的内容返回相应的state
	return {
		...state,
		state变化值
	}
}

export default combineReducers({
	myState
})
```



`store/actions/index.ts`

```
import { ThunkAction } from "redux-thunk"

type RootAction = {
	type: "XXX_XXX",
	payload: {}
}

export const myAction = (): ThunkAction<voie, RootState自定义, unknown, RootAction自定义> => {
	return (dispatch) => {
		dispatch(action) // 转入reducer执行
	}
}
```



基础使用

```
注入store:
	import { Provider } from "react-redux"
	import store from "./store"
	render(<Provider store={store}> <App /> </Provider>)


import { useDispatch, useSelector } from "react-redux"

const dispatch = useDispatch()
dispatch(action)

const xxx = useSelector((state) => state.xxx)
```



### Antd

安装

```
npm install antd @ant-design/icons
```



基础使用

```
入口引入:
	import "antd/dist/antd.css"
```



### Axios







### Icon-park

### Sass





