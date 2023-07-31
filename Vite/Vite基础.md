# Vite基础

Sylvie233的Vite学习~~~

> Author: Sylvie233
>
> Date: 2022/10/16

[TOC]

## 基础介绍



esbuild打包器



原生ESM的HMR



启动

```
pnpm create vite
```



依赖预构建





### vite

```
vite:
	--base:
	--force:
	--host:
	--mode:
	build:
	preview:
```





## 核心内容

vite.config.js

```

```







### 配置文件

#### 基础配置

```js
{
  root: process.cwd(), // 项目根目录（index.html 文件所在的位置）,
  base: '/', // 开发或生产环境服务的公共基础路径 配置引入相对路径
  mode: 'development', // 模式
  plugins: [vue()], // 需要用到的插件数组
  publicDir: 'public', // 静态资源服务的文件夹
  cacheDir: 'node_modules/.vite', // 存储缓存文件的目录
  resolve: {
    alias: [ // 文件系统路径别名
      {
        find: /\/@\//,
        replacement: pathResolve('src') + '/'
      }
    ],
    dedupe: [], // 强制 Vite 始终将列出的依赖项解析为同一副本
    conditions: [], // 解决程序包中 情景导出 时的其他允许条件
    mainFields: [], // 解析包入口点尝试的字段列表
    extensions: ['.mjs', '.js', '.ts', '.jsx', '.tsx', '.json'], // 导入时想要忽略的扩展名列表
    preserveSymlinks: false, // 启用此选项会使 Vite 通过原始文件路径确定文件身份
  },
  css: {
    modules: {
      scopeBehaviour: 'global' | 'local',
      // ...
    },
    postcss: '', // 内联的 PostCSS 配置 如果提供了该内联配置，Vite 将不会搜索其他 PostCSS 配置源
    preprocessorOptions: { // css的预处理器选项
      scss: {
        additionalData: `$injectedColor: orange;`
      }
    }
  },
  json: {
    namedExports: true, // 是否支持从.json文件中进行按名导入
    stringify: false, //  开启此项，导入的 JSON 会被转换为 export default JSON.parse("...") 会禁用按名导入
  },
  esbuild: { // 最常见的用例是自定义 JSX
    jsxFactory: 'h',
    jsxFragment: 'Fragment'
  },
  assetsInclude: ['**/*.gltf'], // 指定额外的 picomatch 模式 作为静态资源处理
  logLevel: 'info', // 调整控制台输出的级别 'info' | 'warn' | 'error' | 'silent'
  clearScreen: true, // 设为 false 可以避免 Vite 清屏而错过在终端中打印某些关键信息
  envDir: '/', // 用于加载 .env 文件的目录
  envPrefix: [], // 以 envPrefix 开头的环境变量会通过 import.meta.env 暴露在你的客户端源码中
  server: {
    host: '127.0.0.1', // 指定服务器应该监听哪个 IP 地址
    port: 5000, // 指定开发服务器端口
    strictPort: true, // 若端口已被占用则会直接退出
    https: false, // 启用 TLS + HTTP/2
    open: true, // 启动时自动在浏览器中打开应用程序
    proxy: { // 配置自定义代理规则
      '/api': {
        target: 'http://jsonplaceholder.typicode.com',
        changeOrigin: true,
        rewrite: (path) => path.replace(/^\/api/, '')
      }
    },
    cors: true, // 配置 CORS
    force: true, // 强制使依赖预构建
    hmr: { // 禁用或配置 HMR 连接
      // ...
    },
    watch: { // 传递给 chokidar 的文件系统监听器选项
      // ...
    },
    middlewareMode: '', // 以中间件模式创建 Vite 服务器
    fs: {
      strict: true, // 限制为工作区 root 路径以外的文件的访问
      allow: [], // 限制哪些文件可以通过 /@fs/ 路径提供服务
      deny: ['.env', '.env.*', '*.{pem,crt}'], // 用于限制 Vite 开发服务器提供敏感文件的黑名单
    },
    origin: 'http://127.0.0.1:8080/', // 用于定义开发调试阶段生成资产的 origin
  },
  build: {
    target: ['modules'], // 设置最终构建的浏览器兼容目标
    polyfillModulePreload: true, // 是否自动注入 module preload 的 polyfill
    outDir: 'dist', // 指定输出路径
    assetsDir: 'assets', // 指定生成静态文件目录
    assetsInlineLimit: '4096', // 小于此阈值的导入或引用资源将内联为 base64 编码
    cssCodeSplit: true, // 启用 CSS 代码拆分
    cssTarget: '', // 允许用户为 CSS 的压缩设置一个不同的浏览器 target 与 build.target 一致
    sourcemap: false, // 构建后是否生成 source map 文件
    rollupOptions: {}, // 自定义底层的 Rollup 打包配置
    lib: {}, // 构建为库
    manifest: false, // 当设置为 true，构建后将会生成 manifest.json 文件
    ssrManifest: false, // 构建不生成 SSR 的 manifest 文件
    ssr: undefined, // 生成面向 SSR 的构建
    minify: 'esbuild', // 指定使用哪种混淆器
    terserOptions: {}, // 传递给 Terser 的更多 minify 选项
    write: true, // 启用将构建后的文件写入磁盘
    emptyOutDir: true, // 构建时清空该目录
    brotliSize: true, // 启用 brotli 压缩大小报告
    chunkSizeWarningLimit: 500, // chunk 大小警告的限制
    watch: null, // 设置为 {} 则会启用 rollup 的监听器
  },
  preview: {
    port: 5000, // 指定开发服务器端口
    strictPort: true, // 若端口已被占用则会直接退出
    https: false, // 启用 TLS + HTTP/2
    open: true, // 启动时自动在浏览器中打开应用程序
    proxy: { // 配置自定义代理规则
      '/api': {
        target: 'http://jsonplaceholder.typicode.com',
        changeOrigin: true,
        rewrite: (path) => path.replace(/^\/api/, '')
      }
    },
    cors: true, // 配置 CORS
  },
  optimizeDeps: {
    entries: [], // 指定自定义条目——该值需要遵循 fast-glob 模式
    exclude: [], // 在预构建中强制排除的依赖项
    include: [], // 可强制预构建链接的包
    keepNames: false, // true 可以在函数和类上保留 name 属性
  },
  ssr: {
    external: [], // 列出的是要为 SSR 强制外部化的依赖,
    noExternal: '', // 列出的是防止被 SSR 外部化依赖项
    target: 'node', // SSR 服务器的构建目标
  }
}
```





#### React集成配置

tsconfig.node.json子项目配置

```js
import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react'

export default defineConfig({
  plugins: [react()],
})

```







### 项目目录

#### Vue

```
Vue项目:
	/node_modules:
	/public:
		favicon.ico:
	/src:
		/assts:
		/components:
		App.vue:
		main.js:
	.gitignore:
	index.html:
	packaage.json:
	pnpm-lock.yaml:
	vite.config.js:
```



配置文件

```
import { defineConfig } from "vite"
import vue from "@vitejs/plugin-vue"
import vueJsx from "@vitejs/plugin-vue-jsx"
import legacy from "@vitejs/plugin-legacy" // 降级兼容浏览器

export default defineConfig({
	resolve: {
		alias: {
			"@xxx": "路径别名"
		},
	},
	cacheDir: "./.cache",
	build: {
		rollupOptions: {
			input: { // 输入文件
				main: "xxx.html",
				xxx: "路径",
			}
		},
		target: "es2015",
	},
	
	
	css: {
		modules: {
			localsConvention: "camelCase",	
		},
	},
	
	
	plugins: [
		vue(),
		vueJsx(),
		legacy({
			targets: [
				"defaults",
				""
			],
		}),
	],
	
	
	optimizeDeps: {
		include: [
			"esm-dep",
		],
	},
})
```



#### Vue-Ts

```
Vue-Ts项目:
	/node_modules:
	/public:
	/src:
		/assets:
		/components:
		App.vue:
		env.d.ts:
		main.ts:
	.gitignore:
	index.html:
	package.json:
	pnpm-lock.yaml:
	tsconfig.json:
	tsconfig.node.json:
	vite.config.ts:
```



env.d.ts

```
/// <reference types="vite/client" />

interface ImportMetaEnv { // import.meta.env类型定义

}
```





vite.config.ts

```

```



tsconfig.json

```
{
	"compilerOptions": {
		"target": "esnext",
		"useDefineForClassFields": true,
		"module": "esnext",
		"moduleResolution": "node",
		"strict": true,
		"jsx": "preserve",
		"sourceMap": true,
		"resolveJsonModule": true,
		"esModuleInterop": true,
		"lib": ["esnext", "dom"],
		"isolatedModules": true,
	},
	"include": [
		"src/**/*.ts",
		"src/**/*.d.ts",
		"src/**/*.tsx",
	],
	"references": [
		{
			"path": "./tsconfig.node.json",
		},
	],
}
```



tsconfig.node.json

```
{
	"compilerOptions": {
		"composite": true,
		"module": "esnext",
		"moduleResolution": "node",
	},
	"include": [
		"vite.config.ts",
	],
}
```



#### React

```
React项目:
	/node_modules:
	/src:
		App.css:
		App.jsx:
		favicon.svg:
		index.css:
		logo.svg:
		main.jsx:
	.gitignore:
	index.html:
	package.json:
	pnpm-lock.yaml:
	vite.config.js:
```



配置文件

```
import { defineConfig } from "vite"
import react from "@vitejs/plugin-react"

export default defineConfig({
	plugins: [
		react(),
	],
})
```





### 缓存

`/node_modules/.vite`





### 模块热重载

#### ImportMeta

```
import.meta
	env:
		BASE_URL:
		SSR:
		Mode:
		DEV:
		PROD:
	hot:
        data: 模块内变量
        accept(): 开始热更新钩子
        decline():
        dispose(): 结束热更新钩子
        invalidate():
    url:
    glob():
    globEager():
```



### 环境变量

`.env`

```

```





### ts集成



### Postcss

`postcss.config.js`

```
module.exports = {
	plugins: [
		require("postcss-nested"),
	]
}
```



### css预处理器

内置支持预处理器，只需按照对应依赖即可直接使用



### Eslint

```
npm i eslint eslint-config-stand eslint-plugin-node eslint-plugin-promise es-plugin-import 
```



`.eslintrc.js`

```
module.exports = {
	extends: "standard",
	rules: {
		"space-before-function-paren": "off",
		"no-undef": "off",
	},
}
```



prettier工具

`.prettierrc`

```
{
	"semi": false,
	
}
```







### 静态资源

- ?url
- ?raw







### WebWorker

- ?worker

直接实例化即可



```
const worker = new Worker("./xxx.js")
worker.onmessage = ev => {
	ev.data
}
```



### WebAssembly



### Git Husky

```
npm i husky
```



husky

```
husky:
	add:
		.husky/pre-commit:
	install:
```



















## API

```
vite:
	defineCOnfig:
```





















