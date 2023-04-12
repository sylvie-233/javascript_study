# Typescript基础

Sylvie233的Typescript学习~~~

> Author: Sylvie233
>
> Date: 2022/10/17

[TOC]

## 基础介绍

安装依赖：

`npm i typescript -g`



编译.ts文件

`tsc xxx.ts`



直接执行.ts文件

`npm i ts-node -g`

`ts-node xxx.ts`



### tsc

```
tsc:
	--init:
	
```



### ts-node

```
ts-node:
	
```





## 核心内容

```
{
	"compilerOptions": {
		"baseUrl": "./",
		"path": {
			"@/*": ["src/*"],
		},
	},
	extends: "./xxx.tsconfig.json",
}
```



### 基础数据类型

1. string
2. number
3. boolean
4. void/undefined/null
5. any/unknown
6. never
7. Array/Function/Symbol/ object/





### 数组

```typescript
let arr: string[] = [1, 2, 3]

let arr: Array<number> = []
```

多维数组





### 元组

```
let arr: [string, number] = ["233", 1]

```





### 枚举

```
enum Xxx {
	a, 
	b = 3, 
	c
}

Xxx.a
```



增长枚举值



字符串枚举

```
enum Xxx {
	a = "233"
}
```



异构枚举：

枚举值类型不一样



const枚举

```
const enum Xxx {
	a,
}
```



反向映射

```
Xxx[0] = Xxx.a
```



### Symbol

唯一标号

```
let xxx:symbol = Symbol("xxx")

// 获取对象中的symbol属性
Object.getOwnPropertySymbols(obj)
```



迭代器

```
let it: Iterator<T> = arr[Symbol.iterator]()

it.next()
{value, done}

for (let item of arr) {
	
}
```







### 函数

```typescript
function func(arg: string): string {
    
}


```

可选参数

函数重载







### 类与对象

```typescript
class Xxx {
    name: string
    constructor(arg: string) {
        this.name = arg
    }
}
```



访问修饰符：

- public
- private
- protected



继承：

```
class A extends B {

}
```

super关键字





实现接口：

```
class A implements B {

}
```





静态属性/静态方法：

直接通过类名访问



抽象类：

```
abstract class Xxx {

}
```

抽象类无法实例化









### 接口

```typescript
interface Xxx {
	name: string
    
}
```

可选属性

属性索引

```
interface Xxx {
	[prop: string]: string
}
```

只读属性readonly

接口继承extends



### 泛型

函数泛型

```
function func<T>() {

}
```



泛型类

```

```





泛型接口

```

```





泛型约束

```
<A extends B>
```



### Mixins混入

对象混入

```
Object.assign()
```



类混入

```
class A implements B, C {}
```



### Decorator装饰器

@xxx

高阶函数



类装饰器

```
const xxx: ClassDecorator = (target: Function) => {

}
```



属性装饰器

```
const xxx: PropertyDecorator = (target: Object, propertyKey: string | symbol) => {

}
```



方法装饰器

```
const xxx: MethodDecorator = (target, key, props) => {

}
```



参数装饰器

```
const xxx: ParameterDecorator = (target, key, index) => {

}
```







### 命名空间

```
namespace A {
	export const a = 1
}


A.a
```



嵌套命名空间



简化命名空间

```
import XXX = A.B
```



命名空间合并

namespace定义合并



三斜线指令

引入命名空间

```
///<reference path="xxx.ts" />
```

引入声明文件

```
///<reference types="node" />
```









### 类型推论



### 类型别名

```
type xxx = xxx
```

字面量类型别名







### 联合类型

```
let xxx: string | number = "233"
```



### 交叉类型

对象属性的并集

```
let xxx: Student | Man = xxx
```



### 类型断言

```
xxx as type

// 强转
<type> xxx
```



### 工具类型

#### 1.Partial

可选属性

```
type Partial<T> = {
	[P in keyof T]?: T[P]
}
```



#### 2.Pick

取出属性

```
type Pick<T, K extends keyof T> = {
	[P in K]: T[P]
}
```



#### 3.Readonly

只读属性

```
type Readonly<T> = {
	readonly [P in keyof T]: T[P]
}
```





#### 4.Record

数据对K-V

```
type Record<K extends keyof any, T> = {
	[P in K]: T;
}
```









### 内置关键字

#### 1.keyof

联合类型

```
<A extends keyof B>


```





#### 2.infer

占位符，类型引用

```
type MyType<T> = T extends Array<infer U> ? U : T
```







## 常用对象

```
:
	JSX:
		Element:
```



### RegExp



### Date



### Error



### Dom对象

```
HTMLElemnt
NodeList


```



### Promise

```
new Promise<T>((resolve, reject) => {

})
```



### Object

```
Object.assign()


Object.getOnwPropertyNames()



```





### Reflect

```
Reflect.get(target, prop, receiver)


Reflect.set(target, prop, val, receiver)
```





### Set

```
let set: Set<T> = new Set([1, 2, 3])
```





### Map

```
let map: Map<T1, T2> = new Map()

map.set(k, val)

```



### Proxy

```
new Proxy(obj, {
	get (target, prop, receiver) {
	
	},
	set (target, prop, val, receiver) {
	
	}
})
```







## 配置文件

tsconfig.json

基础配置

```json
{
    "compilerOptions": {
      "incremental": true, // TS编译器在第一次编译之后会生成一个存储编译信息的文件，第二次编译会在第一次的基础上进行增量编译，可以提高编译的速度
      "tsBuildInfoFile": "./buildFile", // 增量编译文件的存储位置
      "diagnostics": true, // 打印诊断信息 
      "target": "ES5", // 目标语言的版本（ESNext|）
      "module": "CommonJS", // 生成代码的模板标准
      "outFile": "./app.js", // 将多个相互依赖的文件生成一个文件，可以用在AMD模块中，即开启时应设置"module": "AMD",
      "lib": ["DOM", "ES2015", "ScriptHost", "ES2019.Array"], // TS需要引用的库，即声明文件，es5 默认引用dom、es5、scripthost,如需要使用es的高级版本特性，通常都需要配置，如es8的数组新特性需要引入"ES2019.Array",(DOM|DOM.Iterable|ESNext)
      "allowJS": true, // 允许编译器编译JS，JSX文件
      "checkJs": true, // 允许在JS文件中报错，通常与allowJS一起使用
      "outDir": "./dist", // 指定输出目录
      "rootDir": "./", // 指定输出文件目录(用于输出)，用于控制输出目录结构
      "declaration": true, // 生成声明文件，开启后会自动生成声明文件
      "declarationDir": "./file", // 指定生成声明文件存放目录
      "emitDeclarationOnly": true, // 只生成声明文件，而不会生成js文件
      "sourceMap": true, // 生成目标文件的sourceMap文件
      "inlineSourceMap": true, // 生成目标文件的inline SourceMap，inline SourceMap会包含在生成的js文件中
      "declarationMap": true, // 为声明文件生成sourceMap
      "typeRoots": [], // 声明文件目录，默认时node_modules/@types
      "types": [], // 加载的声明文件包
      "removeComments":true, // 删除注释 
      "noEmit": true, // 不输出文件,即编译后不会生成任何js文件
      "noEmitOnError": true, // 发送错误时不输出任何文件
      "noEmitHelpers": true, // 不生成helper函数，减小体积，需要额外安装，常配合importHelpers一起使用
      "importHelpers": true, // 通过tslib引入helper函数，文件必须是模块
      "downlevelIteration": true, // 降级遍历器实现，如果目标源是es3/5，那么遍历器会有降级的实现
      "strict": true, // 开启所有严格的类型检查
      "alwaysStrict": true, // 在代码中注入'use strict'
      "noImplicitAny": true, // 不允许隐式的any类型
      "strictNullChecks": true, // 不允许把null、undefined赋值给其他类型的变量
      "strictFunctionTypes": true, // 不允许函数参数双向协变
      "strictPropertyInitialization": true, // 类的实例属性必须初始化
      "strictBindCallApply": true, // 严格的bind/call/apply检查
      "noImplicitThis": true, // 不允许this有隐式的any类型
      "noUnusedLocals": true, // 检查只声明、未使用的局部变量(只提示不报错)
      "noUnusedParameters": true, // 检查未使用的函数参数(只提示不报错)
      "noFallthroughCasesInSwitch": true, // 防止switch语句贯穿(即如果没有break语句后面不会执行)
      "noImplicitReturns": true, //每个分支都会有返回值
      "esModuleInterop": true, // 允许export=导出，由import from 导入,支持使用import d from 'cjs'的方式引入commonjs包。
      "allowUmdGlobalAccess": true, // 允许在模块中全局变量的方式访问umd模块
      "moduleResolution": "node", // 模块解析策略，ts默认用node的解析策略，即相对的方式导入
      "baseUrl": "./", // 解析非相对模块的基地址，默认是当前目录
      "paths": { // 路径映射，相对于baseUrl
        // 如使用jq时不想使用默认版本，而需要手动指定版本，可进行如下配置
        "jquery": ["node_modules/jquery/dist/jquery.min.js"]
      },
      "rootDirs": ["src","out"], // 将多个目录放在一个虚拟目录下，用于运行时，即编译后引入文件的位置可能发生变化，这也设置可以虚拟src和out在同一个目录下，不用再去改变路径也不会报错
      "listEmittedFiles": true, // 打印输出文件
      "listFiles": true,// 打印编译的文件(包括引用的声明文件)
      "useDefineForClassFields": true,//类属性定义使用Object.DefineProperty()
      "skipLibCheck": true,//跳过.d.ts声明文件的类型检查
      "allowSyntheticDefaultImports": true,//允许有没有默认导出的模块导入
      "forceConsistentCasingInFileNames": true,//强制代码中使用的模块文件名必须和文件系统中的文件名保持大小写一致
      "resolveJsonModule": true,//允许在ts模块中导入 JSON 文件。
        "isolatedModules": true,// 确定ts文件为一个模块文件，而非全局脚本（import,export）
        "jsx": "react-jsx", //设置jsx模式（react-jsx|）
    },

    // 指定一个匹配列表（属于自动指定该路径下的所有ts相关文件）
    "include": [
       "src/**/*"
    ],
    // 指定一个排除列表（include的反向操作）
     "exclude": [
       "demo.ts"
    ],
    // 指定哪些文件使用该配置（属于手动一个个指定文件）
     "files": [
       "demo.ts"
    ],
    // ts子项目配置
    "references": [{ 
        "path": "./tsconfig.node.json" 
    }]
}
```



ts文件编译目标：

compilerOptions.target



指定编译文件目录

includes



指定编译文件

files



指定编译输出目录

compilerOptions.outDir



指定ts模块方式

compilerOptions.module



生成sourceMap

compilerOptions.sourceMap



开启严格模式

compilerOptions.strict



指定输出文件

compilerOptions.outFile



编译后移出注释

compilerOptions.removeComments



开启装饰器功能

compilerOptions.experimentalDecorators





## 声明文件

.d.ts文件

```
declare module xxx {

}



```



declare关键字



package.json中的types字段指定包的声明文件



@types包



### 三斜线指令

```ts
/// <reference types="vite/client" />


/// <reference path="./video" />
```













## 知识点补充

### rollup构建

rollup.config.js

```


export default {
	input: "",
	output: {
		file,
		format,
	}
	plugins: [
		
	]
}
```





### Webpack构建

webpack.config.js

```


module.exports = {
	entry,
	mode,
	output: {
		path,
		filename,
	},
	module: {
		rules: [
			{
				test,
				use,
			}
		]
	},
	devServer: {
		port,
		proxy: {
			
		}
	},
	resolve: {
		
	},
	
}
```











