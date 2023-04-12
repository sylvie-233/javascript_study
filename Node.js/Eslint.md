# Eslint基础

> Author: Sylvie233
>
> Date: 23/03/10
>

[TOC]

## 基础介绍







### eslint

```
eslint:
	--ext:
		js:
	--init:
```





## 核心内容

`.eslintrc.js`

```
{
	env: {
		browser: true,
		es2021: true,
	},
	extends: [
			"airbnb-base"
    ],
	parserOptions: {
		ecmaVersion: 12,
		sourceType: module,
	},
	rules: {
		no-console: 0,
	},
	globals: {
		
	},
}
```



