[toc]

# `React`全家桶(技术栈)

尚硅谷前端研究院  [新版本 `React` 16.8  2021版]



## 第1章：`React`入门 

### 1.1.`React`简介

#### 1.1.1官网

- 1.[英文官网](https://reactjs.org/)
- 2.[中文官网](https://react.docschina.org/)

#### 1.1.2  介绍描述

- 1.用于动态构建用户界面的 `JavaScript` 库(只关注于视图)  
    - 1、发送请求获取数据，
    - 2、处理数据（过滤，整理格式等 
    - 3、<font color="red">操作`DOM`呈现页面</font> `React` 只负责这部分 )
    - 4、<font color="red">核心：`React` 是一个将数据渲染为 `HTML` 视图的开源 `JavaScript` 库</font>

- 2.由 `Facebook` 开源

#### <font color="orange">1.1.3为什么学`React`,原生 `JS` 的痛点?</font>

- 原生 `JS` 操作`DOM`繁琐，效率低（<font color="red">`DOM-API` 操作 `UI`</font>）
- 使用 `JS` 直接操作`DOM`，浏览器会进行大量的<font color="red">重绘重排</font>。
- 原生 `JS` 没有<font color="red">组件化</font>编码方案，代码复用率低。

#### 1.1.4为什么学`React`,`React` 的特点？

- 1.采用 <font color="red">__声明式编码__ __组件化模式__</font>，提高开发效率及组件复用率
- 3.在`React Native` 中可以使用 `React` 语法进行 移动端开发 
- 4.使用  <font color="red">__虚拟`DOM`__</font> +优秀的  <font color="red">__`Diffing`算法__</font>，尽量减少与真实`DOM` 的交互

#### 1.1.5`React` 高效的原因

- 1.使用虚拟(`virtual`)`DOM`, 不总是直接操作页面真实`DOM`。

- 2.`DOM Diffing`算法, 最小化页面重绘。

#### 1.1.6 学习 `React` 之前你要掌握的`js`基础知识

- 判断 `this` 的指向
- `class`（类）
- `ES6` 语法规范
- `npm` 包管理器
- 原型机原型链
- 数组常用方法
- 模块化


### 1.2.`React`的基本使用

#### 1.2.1  效果 `Hello React`！

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>Hello React</title>
	</head>
	<body>
		<!-- 注意一!!--必须有容器div -->
		<div id="test">
			
		</div>
		<!-- `React`核心库。（ 注意二!!--核心库先于下面两个引入 ） -->
		<script src="./react_js/react.development.js" type="text/javascript" charset="utf-8"></script>

        <!-- 提供操作`DOM`的`react`扩展库 -->
		<script src="./react_js/react-dom.development.js" type="text/javascript" charset="utf-8"></script>

        <!-- 解析`JSX`语法代码转为`JS`代码的库。( Script 标签必须 type=“text/babel”) -->
		<script src="./react_js/babel.min.js" type="text/javascript" charset="utf-8"></script>
		
		<script type="text/babel">/*  注意三!!--这里必须是 babel  */
			// 创建虚拟Dom
			const vDom = <h1>Hello React!</h1>  /*   注意四!!--此处一定不要写引号 因为不是字符串 */
			
			//渲染虚拟Dom
			ReactDOM.render(vDom,document.getElementById('test'))
			
		</script>
	</body>
</html>

```

#### 1.2.2.相关`js`库

- <font color="red">**`react.js`**</font>：`React`核心库。（ **核心库先于下面两个引入** ）
- <font color="red">**`react-dom.js`**</font>：提供操作`DOM`的`react`扩展库。
- <font color="red">**`babel.min.js`**</font>：解析`JSX`语法代码转为`JS`代码的库。(`Script`标签必须`type=“text/babel”`)

#### 1.2.3.创建虚拟`DOM`的两种方式

- 1.纯<font color="red">**`JS`**</font>方式(一般不用):  

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8">
    <title>使用js创建虚拟DOM的两种方式</title>
</head>
<body>
    <!-- 必须有容器div -->
    <div id="test">
        
    </div>
    
    <script src="./react_js/react.development.js" type="text/javascript" charset="utf-8"></script>
    <script src="./react_js/react-dom.development.js" type="text/javascript" charset="utf-8"></script>

    
    <script type="text/javascript">
        // js创建虚拟Dom
        const vDom = React.createElement('h1',{id:"title"},"Hello React")
        
        // 如果h1标签嵌套其他标签 必须使用React.createElement()去实现
        
        //渲染虚拟Dom
        ReactDOM.render(vDom,document.getElementById('test'))
        
    </script>
</body>
</html>

```
- 2.<font color="red">**`JSX `**</font>方式

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8">
    <title>使用  jsx  创建 虚拟 DOM 的两种方式</title>
</head>
<body>
<!-- 必须有容器div -->
<div id="test">
    
</div>
    
<script src="./react_js/react.development.js" type="text/javascript" charset="utf-8"></script>
<script src="./react_js/react-dom.development.js" type="text/javascript" charset="utf-8"></script>
<script src="./react_js/babel.min.js" type="text/javascript" charset="utf-8"></script>
    
<script type="text/babel">/*  这里必须是babel  */
    // 创建虚拟Dom
    const vDom = (
    <h1 id="title">
        <span>Hello React!</span>
    </h1>
    )  /*   此处一定不要写引号 因为不是字符串 */
    
    //渲染虚拟Dom
    ReactDOM.render(vDom,document.getElementById('test'))
    
</script>
</body>
</html>

```

#### 1.2.4.虚拟`DOM`与真实`DOM`

- 1.`React`提供了一些`API`来创建一种 “特别” 的一般`js`对象
    - <font color="red">`const VDOM = React.createElement('xx',{id:'xx'},'xx')`</font>
    - 上面创建的就是一个简单的虚拟`DOM`对象

- 2.虚拟`DOM`对象最终都会被`React`转换为真实的`DOM`

- 3.我们编码时基本只需要操作`react`的虚拟`DOM`相关数据, `react`会转换为真实`DOM`变化而更新界。
(`debugger`  鼠标放在`TDOM`上，可看到真实`DOM`上有很多属性，而虚拟`DOM`上属性很少。)

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>虚拟DOM与真实DOM</title>
	</head>
	<body>
		<!-- 必须有容器div -->
		<div id="test">
			
		</div>
		<div id="demo">
			
		</div>
		
		<script src="./react_js/react.development.js" type="text/javascript" charset="utf-8"></script>
		<script src="./react_js/react-dom.development.js" type="text/javascript" charset="utf-8"></script>
		<script src="./react_js/babel.min.js" type="text/javascript" charset="utf-8"></script>
		
		<script type="text/babel">/*  这里必须是babel  */

			// 创建虚拟Dom
			const vDom = (
			<h1 id="title">
				<span>Hello React!</span>
			</h1>
			)  /*   此处一定不要写引号 因为不是字符串 */
			
			//渲染虚拟Dom
			ReactDOM.render(vDom,document.getElementById('test'))
			
			const  TDOM = document.getElementById('demo')
			console.log('虚拟DOM',vDom)
			console.log('真实',TDOM)
			debugger;
			console.log('类型',typeof vDom)
			console.log('vDOM',vDom instanceof Object)
			
			/* 关于虚拟DOM:
			虚拟DOM其实就是Object类型的对象（一般对象）
			虚拟DOM比较轻，真实DOM比较重，因为虚拟DOM是react内部使用，无需真实DOM那么多属性。
			虚拟DOM最终会被React 转化为真实DOM
			*/
			
		</script>
	</body>
</html>

```

### 1.3.`React JSX`

#### 1.3.1.效果


#### 1.3.2  <font color="red">`JSX`</font>

- 1、**全称**:  `JavaScript XML`

- 2、**`react`定义的一种类似于`XML`的`JS`扩展语法**: `JS` + `XML`本质是<font color="red">`React.createElement(component, props, ...children)`</font>方法的语法糖

- 3、**作用**: 用来简化创建虚拟`DOM`
    - 1、**写法**：<font color="red" size='4'>`const vDom = <h1>Hello React!</h1>`</font>
    - 2、**注意1**：它不是字符串, 也不是`HTML`/`XML`标签
    - 3、**注意2**：它最终产生的就是一个<font color="red">`JS`</font>对象<font color="red">  `Script`标签必须`type=“text/babel”`</font>

- 4、标签名任意: `HTML`标签或其它标签

- 5、标签属性任意: `HTML`标签属性或其它

- 6、基本语法规则
    - 1、遇到   <font color="red">`<`</font>   开头的代码, 以  <font color="red">标签</font>  的语法解析:<font color="red"> `html`同名标签转换为`html`同名元素, 其它标签需要特别解析</font>
    - 2、遇到以  <font color="red"> `{ `</font>   开头的代码，以    <font color="red">`JS`</font>  语法解析:<font color="red"> 标签中的`js`表达式必须用`{}`包含</font>
    - 3、样式类名指定<font color="red">不要使用`class`</font>，而是<font color="red">`className`</font>；内联样式的话，使用<font color="red">`style={{marginLfet:’10px’}}`</font>,`key`小驼峰
    - 4、只能有一个根标签
    - 5、标签必须闭合
    - **6、标签首字母**：
      - 如果<font color="red">首字母为小写</font>，则将该标签转为`html`同名标签，如果`html`无该标签对应的同名元素，则报错。
      - 如果<font color="red">首字母大写</font>，`React`就去渲染对应的组件，
      - 如果<font color="red">组件没有定义</font>，则报错。
```HTML
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>JSX语法</title>
		<style type="text/css">
			.title{
				background: #035D68;
			}
		</style>
	</head>
	<body>
<!-- 必须有容器div -->
<div id="test">
    
</div>

<script src="./react_js/react.development.js" type="text/javascript" charset="utf-8"></script>
<script src="./react_js/react-dom.development.js" type="text/javascript" charset="utf-8"></script>
<script src="./react_js/babel.min.js" type="text/javascript" charset="utf-8"></script>

<script type="text/babel">/*  这里必须是babel  */

const myId = "h1TiTle"
const myData = "Hello World!"

// 使用JSX 创建虚拟Dom
const vDom = (
<h1 id={myId.toLowerCase()} className='title'>
    <span style={{fontSize:"14px",color:'#fff'}}>Hello React!----{myData}</span>
    <input />
</h1>
) 

//渲染虚拟Dom到页面
ReactDOM.render(vDom,document.getElementById('test'))
			
// jsx语法规则：
    // 1、定义虚拟DOM时，不要写引号
    // 2、标签中使用js表达式要用{}去解析
    // 3、样式类名指定不要用class，而是用className
    // 4、内联样式，要用style={{key:value}}的形式去写，最外面的{}表示里面为js表达式，里面的{}表示是一个对象
    // 5、不能有多个根标签
    // 6、标签必须闭合
    // 7、标签首字母小写->小写标签jsx就会转为d对应的html同名标签，没有对应的html标签则报错，
    // 8、标签首字母大写->首字母大写的标签jsx就会转为组件名,组件没定义，则报错
		</script>
	</body>
</html>

```

- 7、<font color="red">**`babel.js`**</font>的作用
    - 1、浏览器不能直接解析`JSX`代码, 需要`babel`转译为纯`JS`的代码才能运行
    - 2、只要用了`JSX`，都要加上<font color="red">`type="text/babel"`</font>, 声明需要`babel`来处理



#### 1.3.3.渲染虚拟`DOM`(元素)

虚拟`Dom`本质是`Objec`t类型的对象（一般对象），虚拟`Dom`比较“轻”，真实`Dom`比较 “重”，因为虚拟`Dom`是`React`内部在用，无需真实`Dom`上那么多的属性，虚拟`Dom`最终会被`React`转化为真实`Dom`，展示到页面上

- 1、语法:  <font color="red">`ReactDOM.render(virtualDOM, containerDOM)`</font>
- 2、作用: 将虚拟`DOM`元素渲染到页面中的真实容器`DOM`中显示
- 3、参数说明
    - 1、参数一: 纯`js`或`jsx`创建的虚拟`dom`对象
    - 2、参数二: 用来包含虚拟`DOM`元素的真实`dom`元素对象(一般是一个`div`)
    `React.createElement(‘标签名’，‘标签属性’，标签内容)`

#### 1.3.4.`JSX`练习

需求: 动态展示如下列表

补充回顾： 什么是表达式？什么是`js`语句？区别是什么？

表达式： 会产生一个值，可以放在任何一个需要值的地方：

下面都是表达式：
- 1、`a`
- 2、`a+b`
- 3、`demo(1)`
- 4、`arr.map()`
- 5、`function test(){}`

`js`语句：
下面都是语句（代码）：
- 1、`if(){}}`
- 2、`for(){}`
- 3、`switch(){case:xxx}`

```jsx
//模拟一些数据
const data = ['Angular','React','Vue']
//1.创建虚拟DOM
const VDOM = (
	<div>
		<h1>前端js框架列表</h1>
		<ul>
			{data.map((item,index)=>{
					return <li key={index}>{item}</li>
			})}
		</ul>
	</div>
)
//2.渲染虚拟DOM到页面
ReactDOM.render(VDOM,document.getElementById('test'))
```



### 1.4.模块与组件、模块化与组件化的理解

#### 1.4.1.模块(`js`模块)

- 1.**理解**：向外提供特定功能的`js`程序, 一般就是一个`js`文件

- 2.**为什么要拆成模块**：随着业务逻辑增加，代码越来越多且复杂。

- 3.**作用**：复用`js`, 简化`js`的编写, 提高`js`运行效率

#### 1.4.2.组件

- 1.**理解**：用来实现局部功能效果的代码和资源的集合(`html`/`css`/`js`/`image`等等)

- 2.**为什么要用组件**： 一个界面的功能更复杂

- 3.**作用**：复用编码, 简化项目编码, 提高运行效率

#### 1.4.3.模块化

当应用的`js`都以模块来编写的, 这个应用就是一个模块化的应用

#### 1.4.4.组件化

当应用是以多组件的方式实现, 这个应用就是一个组件化的应用



## 第2章：`React`面向组件编程

### 2.0  复习 class 类

- 1.类中的构造器不是必须要写的，要对实例进行一些初始化的操作，如添加指定属性时才写。

- 2.如果A类继承了B类，且A类中写了构造器，那么A类构造器中的super是必须要调用的。

-  3.类中所定义的方法，都放在了类的原型对象上，供实例去使用。

```js
//创建一个Person类
class Person {
	//构造器方法
	constructor(name,age){
		//构造器中的this是谁？—— 类的实例对象
		this.name = name
		this.age = age
	}
	//一般方法
	speak(){
		//speak方法放在了哪里？——类的原型对象上，供实例使用
		//通过Person实例调用speak时，speak中的this就是Person实例
		console.log(`我叫${this.name}，我年龄是${this.age}`);
	}
}

//创建一个Student类，继承于Person类
class Student extends Person {
	constructor(name,age,grade){
		super(name,age)
		this.grade = grade
		this.school = '尚硅谷'
	}
	//重写从父类继承过来的方法
	speak(){
		console.log(`我叫${this.name}，我年龄是${this.age},我读的是${this.grade}年级`);
		this.study()
	}
	study(){
		//study方法放在了哪里？——类的原型对象上，供实例使用
		//通过Student实例调用study时，study中的this就是Student实例
		console.log('我很努力的学习');
	}
}
```



### 2.1. 基本理解和使用

#### 2.1.1. 使用`React`开发者工具调试

#### 2.1.2. 函数式组件 和 类式组件

- **函数式组件**：

```js
//1--创建函数式组件，必须有返回值
function Demo(){
    return <h2>我是函数式组件！使用与简单组件的定义！</h2>
}

//2--渲染组件到页面
ReactDOM.render(<Demo />,document.getElementById('test'))
//定义的函数 Demo，调用了吗？ React帮你调用了
//es6 babel编译后，开启严格模式后，函数里this为undefined
        

// 渲染时函数组件名 名写成标签的形式,<Demo />并且闭合
// <Demo /> 首字母必须大写,

// 执行了React.render(<>)之后，发生了什么？
// 在React解析组件标签，找到了组件
// 发现组件是使用函数定义的，随后调用了函数
```

- **类式组件**：
  - 执行了`React.render(<MyComponent>)`之后，发生了什么？
  - 1、在React解析  组件标签 ，找到了组件`MyComponent`
  - 2、发现组件是使用类定义的，随后 `new` 出了该类的实例，并通过该实例调用到原型上的 render 方法
  - 3、将 `rander` 返回的虚拟` Dom` 转为真实 `DOM`，随后呈现在页面中。

```js
//1--创建类式组件
class MyComponent extends React.Component{  
    render(){  //render 必须写，必须由返回值
        return (<h2>我是类式组件！适用于复杂组件</h2>)
    }
}

//2--渲染组件到页面
ReactDOM.render(<MyComponent />,document.getElementById('test'))
```

#### 2.1.2 复杂组件和简单组件

- 有状态的组件为复杂组件  (什么是状态？ 组件的状态里存着数据)
- 没状态的组件为简单组件

#### 2.1.3. 注意

- 1.组件名 <font color="red">__必须首字母大写__</font>
- 2.虚拟`DOM`元素<font color="red"> __只能有一个根元素__</font>
- 3.虚拟`DOM`元素<font color="red"> __必须有结束标签__</font>

#### 2.1.4. 渲染类组件标签的基本流程

- 1.<font color="red">`React`内部会创建组件实例对象</font>

- 2.调用<font color="red">`render()`</font>得到虚拟`DOM`, 并解析为真实`DOM`

- 3.插入到指定的页面元素内部

### 2.2. 组件（类组件）三大核心属性1: `state`

#### 2.2.1. 效果

需求: 定义一个展示天气信息的组件

1.默认展示天气炎热 或 凉爽

2.点击文字切换天气

```js
//创建类式组件(有状态的组件就叫复杂组件) 借助构造器初始化状态，读取state 
class Weather extends React.Component {
    constructor(props) {
    	super(props)
    	// 初始化状态
    	this.state = {isHot: false,}
    }
    render() {
        // 读取状态
    const { isHot } = this.state  //解构
    return (
        <div>
        	<div>
            	<h1>{ isHot ? "天气炎热" : "不热" }</h1>
        	</div>
        </div>
    	)
    }
}
        
//渲染组件到页面
ReactDOM.render(<Weather />,document.getElementById('test'))
```
#### 2.2.2. 理解

1、`state`是组件对象最重要的属性, 值是对象(可以包含多个`key-value`的组合)

2、组件被称为"状态机", 通过更新组件的`state`来更新对应的页面显示(重新渲染组件)

#### 2.2.3. 强烈注意

- 1、组件中`render`方法中的`this`为组件实例对象

- 2、组件自定义的方法中`this`为`undefined`，如何解决？

    - a、强制绑定`this`: 通过函数对象的`bind()`
    - b、箭头函数

- 3、状态数据，不能直接修改或更新，使用`setState`

### 2.3. 组件三大核心属性2: `props`

#### 2.3.1. 效果

需求: 自定义用来显示一个人员信息的组件
1、姓名必须指定，且为字符串类型；
2、性别为字符串类型，如果性别没有指定，默认为男
3、年龄为字符串类型，且为数字类型，默认值为18

#### 2.3.2. 理解

1、每个组件对象都会有`props`(`properties`的简写)属性
2、组件标签的所有属性都保存在`props`中

#### 2.3.3. 作用

1、通过标签属性从组件外向组件内传递变化的数据
2、注意: 组件内部不要修改`props`数据

#### 2.3.4. 编码操作

1、内部读取某个属性值

2、对`props`中的属性值进行类型限制和必要性限制
第一种方式（`React v15.5` 开始已弃用）：
第二种方式（新）：使用`prop-types`库进限制（需要引入`prop-types`库）

3、扩展属性: 将对象的所有属性通过props传递

4、默认属性值：

5、组件类的构造函数

### 2.4. 组件三大核心属性3: `refs`与事件处理
#### 2.4.1. 效果

需求: 自定义组件, 功能说明如下:

- 点击按钮, 提示第一个输入框中的值
- 当第2个输入框失去焦点时, 提示这个输入框中的值
  

#### 2.4.2. 理解

- 组件内的标签可以定义<mark>`ref`</mark>属性来标识自己

#### 2.4.3. 编码

1、<mark>字符串形式</mark>的`ref`( 过时的API )

例如： `<input ref="input1" type="text"/>`  表单标签里 使用`ref='标识名'` 打标识，然后使用 `refs.标识名.value` 获取表单值

```jsx
//  创建组件
class Demo extends React.Component{
	//  展示  左侧  输入框的数据
	showData = ()=>{
		const {input1} = this.refs
		alert(input1.value)
	}
	//  展示  右侧  输入框的数据
	showData2 = ()=>{
		const {input2} = this.refs
		alert(input2.value)
	}
	render(){
		return(
			<div>
				<input ref="input1" type="text" placeholder="点击按钮提示数据"/>&nbsp;
				<button onClick={this.showData}>点我提示左侧的数据</button>&nbsp;
				<input ref="input2" onBlur={this.showData2} type="text" placeholder="失去焦点提示数据"/>
			</div>
		)
	}
}
//渲染组件到页面
ReactDOM.render(<Demo a="1" b="2"/>,document.getElementById('test'))
```

2、<mark>回调形式</mark>的`ref`

回调函数有3个特点；一是你定义的，二是你没调用，三是他自己执行了；

例如：`<input ref={c => this.input1 = c } type="text"/>`表单标签里 使用`ref={c => this.input1 = c }`通过 `this.input1.value`获取表单数据

```jsx
//  创建组件
class Demo extends React.Component{
	//  展示  左侧  输入框的数据
	showData = ()=>{
		const {input1} = this
		alert(input1.value)
	}
	//  展示  右侧  输入框的数据
	showData2 = ()=>{
		const {input2} = this
		alert(input2.value)
	}
	render(){
		return(
			<div>
				<input ref={c => this.input1 = c } type="text" placeholder="点击按钮提示数据"/>&nbsp;
				<button onClick={this.showData}>点我提示左侧的数据</button>&nbsp;
				<input onBlur={this.showData2} ref={c => this.input2 = c } type="text" placeholder="失去焦点提示数据"/>&nbsp;
			</div>
		)
	}
}
//渲染组件到页面
ReactDOM.render(<Demo a="1" b="2"/>,document.getElementById('test'))
```

3、回调 ref 中回调执行次数的问题

如果 `ref` 回调函数是以内联函数的方式定义的，在更新过程中它会被执行两次，第一次传入参
数null，然后第二次会传入参数 `DOM` 元素。这是因为在每次渲染时会创建一个新的函数实
例，所以 `React` 清空旧的 `ref` 并且设置新的。通过将 `ref` 的回调函数定义成 `class` 的绑定函数的
方式可以避免上述问题，但是大多数情况下它是无关紧要的。

```jsx
//创建组件
class Demo extends React.Component{
	state = {isHot:false}
	showInfo = ()=>{
		const {input1} = this
		alert(input1.value)
	}
	changeWeather = ()=>{
		//获取原来的状态
		const {isHot} = this.state
		//更新状态
		this.setState({isHot:!isHot})
	}
	saveInput = (c)=>{
		this.input1 = c;
		console.log('@',c);
	}
	render(){
		const {isHot} = this.state
		return(
			<div>
				<h2>今天天气很{isHot ? '炎热':'凉爽'}</h2>
                  {/*  内联函数  */}
				{/*<input ref={(c)=>{this.input1 = c;console.log('@',c);}} type="text"/><br/><br/>*/}
                  {/*  class 类绑定函数  */}
				<input ref={this.saveInput} type="text"/><br/><br/>
				<button onClick={this.showInfo}>点我提示输入的数据</button>
				<button onClick={this.changeWeather}>点我切换天气</button>
			</div>
		)
	}
}
//渲染组件到页面
ReactDOM.render(<Demo/>,document.getElementById('test'))
```



4、<mark>`createRef`创建`ref`</mark>容器·

```jsx
//创建组件
class Demo extends React.Component{
	/* 
		React.createRef调用后可以返回一个容器，该容器可以存储被ref所标识的节点,该容器是“专人专用”的
	 */
	myRef = React.createRef()
	myRef2 = React.createRef()
	//展示左侧输入框的数据
	showData = ()=>{
		alert(this.myRef.current.value);
	}
	//展示右侧输入框的数据
	showData2 = ()=>{
		alert(this.myRef2.current.value);
	}
	render(){
		return(
			<div>
				<input ref={this.myRef} type="text" placeholder="点击按钮提示数据"/>&nbsp;
				<button onClick={this.showData}>点我提示左侧的数据</button>&nbsp;
				<input onBlur={this.showData2} ref={this.myRef2} type="text" placeholder="失去焦点提示数据"/>&nbsp;
			</div>
		)
	}
}
//渲染组件到页面
ReactDOM.render(<Demo a="1" b="2"/>,document.getElementById('test'))
```



```jsx
import { useRef } from 'react';
export default function Form() {
  const inputRef = useRef(null);
  handleClick = () => {
    alert(inputRef.current.value)
  }
  return (
    <>
      <input ref={inputRef} onChange={this.handleClick}/>
    </>
  );
}
```



#### 2.4.4. 事件处理

- 1、通过`onXxx`属性指定事件处理函数(注意大小写)
	- 1、`React`使用的是自定义(合成)事件, 而不是使用的原生`DOM`事件
	- 2、`React`中的事件是通过事件委托方式处理的(委托给组件最外层的元素)
- 2、通过`event.target`得到发生事件的`DOM`元素对象

### 2.5. 收集表单数据
#### 2.5.1. 效果

需求: 定义一个包含表单的组件
输入用户名密码后, 点击登录提示输入信息

#### 2.5.2. 理解

包含表单的组件分类
1.受控组件
2.非受控组件

### 2.6. 组件的生命周期
#### 2.6.1. 效果

需求:定义组件实现以下功能：

1. 让指定的文本做显示 / 隐藏的渐变动画
2. 从完全可见，到彻底消失，耗时2S
3. 点击“不活了”按钮从界面中卸载组件

#### 2.6.2. 理解

1.组件从创建到死亡它会经历一些特定的阶段。
2.`React`组件中包含一系列勾子函数(生命周期回调函数), 会在特定的时刻调用。
3.我们在定义组件时，会在特定的生命周期回调函数中，做特定的工作。

#### 2.6.3. 生命周期流程图(旧)

生命周期的三个阶段（旧）
- 1. 初始化阶段: 由`ReactDOM.render()`触发---初次渲染
    - 1.`constructor()`
    - 2.`componentWillMount()`
    - 3.`render()`
    - 4.`componentDidMount()`
- 2. 更新阶段: 由组件内部`this.setSate()`或父组件重新`render`触发
    - 1.`shouldComponentUpdate()`
    - 2.`componentWillUpdate()`
    - 3.`render()`
    - 4.`componentDidUpdate()`
- 3. 卸载组件: 由`ReactDOM.unmountComponentAtNode()`触发
    - 1.`componentWillUnmount()`

```jsx
//创建组件
class Count extends React.Component{
	//构造器
	constructor(props){
		console.log('Count---constructor');
		super(props)
		//初始化状态
		this.state = {count:0}
	}
	//加1按钮的回调
	add = ()=>{
		//获取原状态
		const {count} = this.state
		//更新状态
		this.setState({count:count+1})
	}
	//卸载组件按钮的回调
	death = ()=>{
		ReactDOM.unmountComponentAtNode(document.getElementById('test'))
	}
	//强制更新按钮的回调
	force = ()=>{
		this.forceUpdate()
	}
	//组件将要挂载的钩子
	componentWillMount(){
		console.log('Count---componentWillMount');
	}
	//组件挂载完毕的钩子
	componentDidMount(){
		console.log('Count---componentDidMount');
	}
	//组件将要卸载的钩子
	componentWillUnmount(){
		console.log('Count---componentWillUnmount');
	}
	//控制组件更新的“阀门”
	shouldComponentUpdate(){
		console.log('Count---shouldComponentUpdate');
		return true
	}
	//组件将要更新的钩子
	componentWillUpdate(){
		console.log('Count---componentWillUpdate');
	}
	//组件更新完毕的钩子
	componentDidUpdate(){
		console.log('Count---componentDidUpdate');
	}
	render(){
		console.log('Count---render');
		const {count} = this.state
		return(
			<div>
				<h2>当前求和为：{count}</h2>
				<button onClick={this.add}>点我+1</button>
				<button onClick={this.death}>卸载组件</button>
				<button onClick={this.force}>不更改任何状态中的数据，强制更新一下</button>
			</div>
		)
	}
}
		
//父组件A
class A extends React.Component{
	//初始化状态
	state = {carName:'奔驰'}
	changeCar = ()=>{
		this.setState({carName:'奥拓'})
	}
	render(){
		return(
			<div>
				<div>我是A组件</div>
				<button onClick={this.changeCar}>换车</button>
				<B carName={this.state.carName}/>
			</div>
		)
	}
}
		
//子组件B
class B extends React.Component{
	//组件将要接收新的props的钩子
	componentWillReceiveProps(props){
		console.log('B---componentWillReceiveProps',props);
	}
	//控制组件更新的“阀门”
	shouldComponentUpdate(){
		console.log('B---shouldComponentUpdate');
		return true
	}
	//组件将要更新的钩子
	componentWillUpdate(){
		console.log('B---componentWillUpdate');
	}
	//组件更新完毕的钩子
	componentDidUpdate(){
		console.log('B---componentDidUpdate');
	}
	render(){
		console.log('B---render');
		return(
			<div>我是B组件，接收到的车是:{this.props.carName}</div>
		)
	}
}
		
//渲染组件
ReactDOM.render(<Count/>,document.getElementById('test'))
```

#### 2.6.4. 生命周期流程图(新)

生命周期的三个阶段（新）

- 1、初始化阶段: 由<font color='red'>ReactDOM.render()</font>触发---初次渲染
    - 1、<font color='red'>constructor()</font>
    - 2、<font color='red'>getDerivedStateFromProps</font>
    - 3、<font color='red'>render()</font>
    - 4、<font color='red'>componentDidMount() </font>

- 2、更新阶段: 由组件内部<font color='red'>this.setSate()</font>或父组件重新<font color='red'>render</font>触发
    - 1、<font color='red'>getDerivedStateFromProps</font>
    - 2、<font color='red'>shouldComponentUpdate()</font>
    - 3、<font color='red'>render()</font>
    - 4、<font color='red'>getSnapshotBeforeUpdate</font>
    - 5、<font color='red'>componentDidUpdate()</font>
- 3、卸载组件: 由<font color='red'>ReactDOM.unmountComponentAtNode()</font>触发
    - 1、<font color='red'>componentWillUnmount()</font>

```jsx
//创建组件
class Count extends React.Component{
	//构造器
	constructor(props){
		console.log('Count---constructor');
		super(props)
		//初始化状态
		this.state = {count:0}
	}
	//加1按钮的回调
	add = ()=>{
		//获取原状态
		const {count} = this.state
		//更新状态
		this.setState({count:count+1})
	}
	//卸载组件按钮的回调
	death = ()=>{
		ReactDOM.unmountComponentAtNode(document.getElementById('test'))
	}
	//强制更新按钮的回调
	force = ()=>{
		this.forceUpdate()
	}			
	//若state的值在任何时候都取决于props，那么可以使用getDerivedStateFromProps
	static getDerivedStateFromProps(props,state){
		console.log('getDerivedStateFromProps',props,state);
		return null
	}
	//在更新之前获取快照
	getSnapshotBeforeUpdate(){
		console.log('getSnapshotBeforeUpdate');
		return 'atguigu'
	}
	//组件挂载完毕的钩子
	componentDidMount(){
		console.log('Count---componentDidMount');
	}
	//组件将要卸载的钩子
	componentWillUnmount(){
		console.log('Count---componentWillUnmount');
	}
	//控制组件更新的“阀门”
	shouldComponentUpdate(){
		console.log('Count---shouldComponentUpdate');
		return true
	}
	//组件更新完毕的钩子
	componentDidUpdate(preProps,preState,snapshotValue){
		console.log('Count---componentDidUpdate',preProps,preState,snapshotValue);
	}			
	render(){
		console.log('Count---render');
		const {count} = this.state
		return(
			<div>
				<h2>当前求和为：{count}</h2>
				<button onClick={this.add}>点我+1</button>
				<button onClick={this.death}>卸载组件</button>
				<button onClick={this.force}>不更改任何状态中的数据，强制更新一下</button>
			</div>
		)
	}
}
		
//渲染组件
ReactDOM.render(<Count count={199}/>,document.getElementById('test'))
```

#### 2.6.5. 重要的勾子

- 1.<font color='red'>`render`</font>：初始化渲染或更新渲染调用
- 2.<font color='red'>`componentDidMount`</font>：开启监听, 发送`ajax`请求
- 3.<font color='red'>`componentWillUnmount`</font>：做一些收尾工作, 如: 清理定时器

#### 2.6.6. 即将废弃的勾子

- 1.<font color='red'>`componentWillMount`</font>
- 2.<font color='red'>`componentWillReceiveProps`</font>
- 3.<font color='red'>`componentWillUpdate`</font>

现在使用会出现警告，下一个大版本需要加上UNSAFE_前缀才能使用，以后可能会被彻底废弃，不建议使用。

#### 4_getSnapShotBeforeUpdate的使用场景

```jsx
class NewsList extends React.Component{
	state = {newsArr:[]}
	componentDidMount(){
		setInterval(() => {
			//获取原状态
			const {newsArr} = this.state
			//模拟一条新闻
			const news = '新闻'+ (newsArr.length+1)
			//更新状态
			this.setState({newsArr:[news,...newsArr]})
		}, 1000);
	}

	getSnapshotBeforeUpdate(){
		return this.refs.list.scrollHeight
	}
	componentDidUpdate(preProps,preState,height){
		this.refs.list.scrollTop += this.refs.list.scrollHeight - height
	}

	render(){
		return(
			<div className="list" ref="list">
				{
					this.state.newsArr.map((n,index)=>{
						return <div key={index} className="news">{n}</div>
					})
				}
			</div>
		)
	}
}
ReactDOM.render(<NewsList/>,document.getElementById('test'))
```



### 2.7. 虚拟  `DOM`  与  `DOM Diffing`  算法

#### 2.7.1. 效果

需求：验证虚拟  `DOM Diffing`  算法的存在

```jsx
class Time extends React.Component {
	state = {date: new Date()}
	componentDidMount () {
		setInterval(() => {
			this.setState({
				date: new Date()
			})
		}, 1000)
	}

	render () {
		return (
			<div>
				<h1>hello</h1>
				<input type="text"/>
				<span>
					现在是：{this.state.date.toTimeString()}
					<input type="text"/>
				</span>
			</div>
		)
	}
}

ReactDOM.render(<Time/>,document.getElementById('test'))
```



#### 2.7.2. 基本原理图

#### 2.7.3 经典面试题:

- 1、 react/vue中的key有什么作用？（key的内部原理是什么？）
- 2、为什么遍历列表时，key最好不要用index?   
  - 1、虚拟DOM中key的作用：
    - 简单的说: key是虚拟DOM对象的标识, 在更新显示时key起着极其重要的作用。
    - 详细的说: 当状态中的数据发生变化时，react会根据【新数据】生成【新的虚拟DOM】, 随后React进行【新虚拟DOM】与【旧虚拟DOM】的diff比较，

> 比较规则如下：
>
> 旧虚拟DOM中找到了与新虚拟DOM相同的key：
>
> - 若虚拟DOM中内容没变, 直接使用之前的真实DOM
>
> - 若虚拟DOM中内容变了, 则生成新的真实DOM，随后替换掉页面中之前的真实DOM
>
>  旧虚拟DOM中未找到与新虚拟DOM相同的key，根据数据创建新的真实DOM，随后渲染到到页面

- 2、用index作为key可能会引发的问题：
  - 若对数据进行：逆序添加、逆序删除等破坏顺序操作:会产生没有必要的真实DOM更新 ==> 界面效果没问题, 但效率低。
  -  如果结构中还包含输入类的DOM：会产生错误DOM更新 ==> 界面有问题。   
  - 注意！如果不存在对数据的逆序添加、逆序删除等破坏顺序操作，仅用于渲染列表用于展示，使用index作为key是没有问题的。
- 3、开发中如何选择key?:
  - 最好使用每条数据的唯一标识作为key, 比如id、手机号、身份证号、学号等唯一值。
  - 如果确定只是简单的展示数据，用index也是可以的。


## 第3章：`React`  应用(基于  `React`  脚手架)

### 3.1. 使用  `create-react-app`  创建  `react`  应用

#### 3.1.1. `react` 脚手架

- 1.xxx脚手架: 用来帮助程序员快速创建一个基于xxx库的模板项目
  - 1.包含了所有需要的配置（语法检查、`jsx`编译、`devServer`…）
  - 2.下载好了所有相关的依赖
  - 3.可以直接运行一个简单效果
- 2.`react`提供了一个用于创建react项目的脚手架库: `create-react-app`
- 3.项目的整体技术架构为:  `react + webpack + es6 + eslint`
- 4.使用脚手架开发的项目的特点: 模块化, 组件化, 工程化

#### 3.1.2. 创建项目并启动

- 第一步，全局安装：<font color="red" size="5">`npm i -g create-react-app`</font>
- 第二步，切换到想创项目的目录，使用命令：<font color="red" size="5">`create-react-app hello-react`</font>
- 第三步，进入项目文件夹：<font color="red" size="5">`cd hello-react`</font>
- 第四步，启动项目：<font color="red" size="5">`npm start`</font>

#### 3.1.3. `react`脚手架项目结构

> `public` ------------------------ 静态资源文件夹
> `favicon.icon` -------------- 网站页签图标
> `index.html` ----------------- 主页面
> `logo192.png` ---------------- logo图
> `logo512.png` ------------------ logo图
> `manifest.json` ---------------- 应用加壳的配置文件
> `robots.txt` ---------------------- 爬虫协议文件
> `src` ------------------------------- 源码文件夹
> `App.css` ------------------------- App组件的样式
> `App.js` --------------------------- App组件
> `App.test.js` -------------------- 用于给App做测试
> `index.css` ---------------------- 样式
> `index.js` ------------------------ 入口文件
> `logo.svg` -------------------------- logo图
> `reportWebVitals.js` --- --- 页面性能分析文件(需要web-vitals库的支持)
> `setupTests.js`  --------------- 组件单元测试的文件(需要jest-dom库的支持)

<font color="red">**小技巧**</font>：

-  快速生成代码片段： VsCode 安装插件  <font color="red">**ES7+ React/Redux/React-Native snippets**</font>
  - <font color="red">rcc</font> 快速生成 类组件 
  - <font color="red">rfc</font> 快速生成函数组件

#### 3.1.4. 功能界面的组件化编码流程（通用）

- 拆分组件: 拆分界面,抽取组件

- 实现静态组件: 使用组件实现静态页面效果

- 实现动态组件
  - 3.1 动态显示初始化数据
    - 3.1.1 数据类型
    - 3.1.2 数据名称
    - 3.1.2 保存在哪个组件?
  - 3.2 交互(从绑定事件监听开始)

### 3.2. 组件的组合使用-TodoList

- 功能: 组件化实现此功能
  - 显示所有todo列表
  - 输入文本, 点击按钮显示到列表的首位, 并清除输入的文本

### 3.3 TodoList 代码

- Header/index.jsx

```jsx
// Header/index.jsx
import React, { Component } from 'react'
import PropTypes from 'prop-types'
import {nanoid} from 'nanoid'
import './index.css'

export default class Header extends Component {

	//对接收的props进行：类型、必要性的限制
	static propTypes = {
		addTodo:PropTypes.func.isRequired
	}

	//键盘事件的回调
	handleKeyUp = (event)=>{
		//解构赋值获取keyCode,target
		const {keyCode,target} = event
		//判断是否是回车按键
		if(keyCode !== 13) return
		//添加的todo名字不能为空
		if(target.value.trim() === ''){
			alert('输入不能为空')
			return
		}
		//准备好一个todo对象
		const todoObj = {id:nanoid(),name:target.value,done:false}
		//将todoObj传递给App
		this.props.addTodo(todoObj)
		//清空输入
		target.value = ''
	}

	render() {
		return (
			<div className="todo-header">
				<input onKeyUp={this.handleKeyUp} type="text" placeholder="请输入你的任务名称，按回车键确认"/>
			</div>
		)
	}
}
```

- Header/index.css

```css
//Header/index.css
/*header*/
.todo-header input {
  width: 560px;
  height: 28px;
  font-size: 14px;
  border: 1px solid #ccc;
  border-radius: 4px;
  padding: 4px 7px;
}

.todo-header input:focus {
  outline: none;
  border-color: rgba(82, 168, 236, 0.8);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 8px rgba(82, 168, 236, 0.6);
}
```



- List/index.jsx

```jsx
// List/index.jsx
import React, { Component } from 'react'
import PropTypes from 'prop-types'
import Item from '../Item'
import './index.css'

export default class List extends Component {

	//对接收的props进行：类型、必要性的限制
	static propTypes = {
		todos:PropTypes.array.isRequired,
		updateTodo:PropTypes.func.isRequired,
		deleteTodo:PropTypes.func.isRequired,
	}

	render() {
		const {todos,updateTodo,deleteTodo} = this.props
		return (

			<ul className="todo-main">
				{
					todos.map( todo =>{
						return <Item key={todo.id} {...todo} updateTodo={updateTodo} deleteTodo={deleteTodo}/>
					})
				}
			</ul>

		)
	}
}
```



- List/index.css

```css
//List/index.css
/*main*/
.todo-main {
  margin-left: 0px;
  border: 1px solid #ddd;
  border-radius: 2px;
  padding: 0px;
}

.todo-empty {
  height: 40px;
  line-height: 40px;
  border: 1px solid #ddd;
  border-radius: 2px;
  padding-left: 5px;
  margin-top: 10px;
}
```

- Item/index.jsx

```jsx
import React, { Component } from 'react'
import './index.css'

export default class Item extends Component {

	state = {mouse:false} //标识鼠标移入、移出

	//鼠标移入、移出的回调
	handleMouse = (flag)=>{
		return ()=>{
			this.setState({mouse:flag})
		}
	}

	//勾选、取消勾选某一个todo的回调
	handleCheck = (id)=>{
		return (event)=>{
			this.props.updateTodo(id,event.target.checked)
		}
	}

	//删除一个todo的回调
	handleDelete = (id)=>{
		if(window.confirm('确定删除吗？')){
			this.props.deleteTodo(id)
		}
	}


	render() {
		const {id,name,done} = this.props
		const {mouse} = this.state
		return (
			<li style={{backgroundColor:mouse ? '#ddd' : 'white'}} onMouseEnter={this.handleMouse(true)} onMouseLeave={this.handleMouse(false)}>
				<label>
					<input type="checkbox" checked={done} onChange={this.handleCheck(id)}/>
					<span>{name}</span>
				</label>
				<button onClick={()=> this.handleDelete(id) } className="btn btn-danger" style={{display:mouse?'block':'none'}}>删除</button>
			</li>
		)
	}
}
```



- Item/index.css

```css
/*item*/
li {
  list-style: none;
  height: 36px;
  line-height: 36px;
  padding: 0 5px;
  border-bottom: 1px solid #ddd;
}

li label {
  float: left;
  cursor: pointer;
}

li label li input {
  vertical-align: middle;
  margin-right: 6px;
  position: relative;
  top: -1px;
}

li button {
  float: right;
  display: none;
  margin-top: 3px;
}

li:before {
  content: initial;
}

li:last-child {
  border-bottom: none;
}
```



- Footer/index.jsx

```jsx
import React, { Component } from 'react'
import './index.css'

export default class Footer extends Component {

	//全选checkbox的回调
	handleCheckAll = (event)=>{
		this.props.checkAllTodo(event.target.checked)
	}

	//清除已完成任务的回调
	handleClearAllDone = ()=>{
		this.props.clearAllDone()
	}

	render() {
		const {todos} = this.props
		//已完成的个数
		const doneCount = todos.reduce((pre,todo)=> pre + (todo.done ? 1 : 0),0)
		//总数
		const total = todos.length
		return (
			<div className="todo-footer">
				<label>
					<input type="checkbox" onChange={this.handleCheckAll} checked={doneCount === total && total !== 0 ? true : false}/>
				</label>
				<span>
					<span>已完成{doneCount}</span> / 全部{total}
				</span>
				<button onClick={this.handleClearAllDone} className="btn btn-danger">清除已完成任务</button>
			</div>
		)
	}
}

```



- Footer/index.css

```css
/*footer*/
.todo-footer {
  height: 40px;
  line-height: 40px;
  padding-left: 6px;
  margin-top: 5px;
}

.todo-footer label {
  display: inline-block;
  margin-right: 20px;
  cursor: pointer;
}

.todo-footer label input {
  position: relative;
  top: -1px;
  vertical-align: middle;
  margin-right: 5px;
}

.todo-footer button {
  float: right;
  margin-top: 5px;
}

```

App.jsx

```jsx
import React, { Component } from 'react'
import Header from './components/Header'
import List from './components/List'
import Footer from './components/Footer'
import './App.css'

export default class App extends Component {
	//状态在哪里，操作状态的方法就在哪里

	//初始化状态
	state = {todos:[
		{id:'001',name:'吃饭',done:true},
		{id:'002',name:'睡觉',done:true},
		{id:'003',name:'打代码',done:false},
		{id:'004',name:'逛街',done:false}
	]}

	//addTodo用于添加一个todo，接收的参数是todo对象
	addTodo = (todoObj)=>{
		//获取原todos
		const {todos} = this.state
		//追加一个todo
		const newTodos = [todoObj,...todos]
		//更新状态
		this.setState({todos:newTodos})
	}

	//updateTodo用于更新一个todo对象
	updateTodo = (id,done)=>{
		//获取状态中的todos
		const {todos} = this.state
		//匹配处理数据
		const newTodos = todos.map((todoObj)=>{
			if(todoObj.id === id) return {...todoObj,done}
			else return todoObj
		})
		this.setState({todos:newTodos})
	}

	//deleteTodo用于删除一个todo对象
	deleteTodo = (id)=>{
		//获取原来的todos
		const {todos} = this.state
		//删除指定id的todo对象
		const newTodos = todos.filter((todoObj)=>{
			return todoObj.id !== id
		})
		//更新状态
		this.setState({todos:newTodos})
	}

	//checkAllTodo用于全选
	checkAllTodo = (done)=>{
		//获取原来的todos
		const {todos} = this.state
		//加工数据
		const newTodos = todos.map((todoObj)=>{
			return {...todoObj,done}
		})
		//更新状态
		this.setState({todos:newTodos})
	}

	//clearAllDone用于清除所有已完成的
	clearAllDone = ()=>{
		//获取原来的todos
		const {todos} = this.state
		//过滤数据
		const newTodos = todos.filter((todoObj)=>{
			return !todoObj.done
		})
		//更新状态
		this.setState({todos:newTodos})
	}

	render() {
		const {todos} = this.state
		return (
			<div className="todo-container">
				<div className="todo-wrap">
					<Header addTodo={this.addTodo}/>
					<List todos={todos} updateTodo={this.updateTodo} deleteTodo={this.deleteTodo}/>
					<Footer todos={todos} checkAllTodo={this.checkAllTodo} clearAllDone={this.clearAllDone}/>
				</div>
			</div>
		)
	}
}

```

App.css

```css
/*base*/
body {
  background: #fff;
}

.btn {
  display: inline-block;
  padding: 4px 12px;
  margin-bottom: 0;
  font-size: 14px;
  line-height: 20px;
  text-align: center;
  vertical-align: middle;
  cursor: pointer;
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.2), 0 1px 2px rgba(0, 0, 0, 0.05);
  border-radius: 4px;
}

.btn-danger {
  color: #fff;
  background-color: #da4f49;
  border: 1px solid #bd362f;
}

.btn-danger:hover {
  color: #fff;
  background-color: #bd362f;
}

.btn:focus {
  outline: none;
}

.todo-container {
  width: 600px;
  margin: 0 auto;
}
.todo-container .todo-wrap {
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 5px;
}

```

### 第4章：`React ajax`

### 4.1. 理解

#### 4.1.1. 前置说明

- 1.`React`本身只关注于界面, 并不包含发送`ajax`请求的代码
- 2.前端应用需要通过`ajax`请求与后台进行交互(`json`数据)
- 3.`react`应用中需要集成第三方`ajax`库(或自己封装)

#### 4.1.2. 常用的`ajax`请求库

- 1.`jQuery`: 比较重, 如果需要另外引入不建议使用
- 2.`axios`: 轻量级, 建议使用
  - 1、封装`XmlHttpRequest`对象的`ajax`
  - 2、`promise`风格
  - 3、可以用在浏览器端和`node`服务器端

### 4.2. `axios`

#### 4.2.1. 文档

[axios  GitHub 库](https://github.com/axios/axios)

#### 4.2.2. 相关`API`

- 1)   `GET`请求

```js
axios.get('/user?ID=12345')
    .then(function (response) {
		console.log(response.data);
	})
	// 
    .catch(function (error) {
	console.log(error);
});

axios.get('/user', {params: {ID: 12345 }} ).then(function (response) {
	console.log(response);
}).catch(function (error) {
    console.log(error);
});
```

- 2)  `POST`请求

```js
axios.post('/user', {
  firstName: 'Fred',
  lastName: 'Flintstone'
})
.then(function (response) {
	console.log(response);
}).catch(function (error) {
	console.log(error);
});
```

### 4.2.2   脚手架代理配置解决跨域

**react脚手架配置代理总结**

**方法一**

> 在package.json中追加如下配置

```json
"proxy":"http://localhost:5000"
```

说明：

- 优点：配置简单，前端请求资源时可以不加任何前缀。

- 缺点：不能配置多个代理。

- 工作方式：上述方式配置代理，当请求了3000不存在的资源时，那么该请求会转发给5000 （优先匹配前端资源）

**方法二**

- 第一步：创建代理配置文件
  - 在`src`下创建配置文件：`src/setupProxy.js`
- 第二步：编写`setupProxy.js`配置具体代理规则：

```js
const proxy = require('http-proxy-middleware')
  module.exports = function(app) {
   app.use(
    proxy('/api1', {  //api1是需要转发的请求(所有带有/api1前缀的请求都会转发给5000)     
    target: 'http://localhost:5000', //配置转发目标地址(能返回数据的服务器地址)
    changeOrigin: true, //控制服务器接收到的请求头中 host 字段的值
     /*
     changeOrigin 设置为 true 时，服务器收到的请求头中的host为：localhost:5000
     changeOrigin  设置为 false 时，服务器收到的请求头中的host为：localhost:3000
     changeOrigin 默认值为 false，但我们一般将changeOrigin值设为true
     */
     pathRewrite: {'^/api1': ''} //去除请求前缀，保证交给后台服务器的是正常请求地址(必须配置)
    }),
    proxy('/api2', { 
     target: 'http://localhost:5001',
     changeOrigin: true,
     pathRewrite: {'^/api2': ''}
    })
   )
  }
```



说明：

- 优点：可以配置多个代理，可以灵活的控制请求是否走代理。
- 缺点：配置繁琐，前端请求资源时必须加前缀。

### 4.3. 案例—github用户搜索

#### 4.3.1. 效果

请求地址: https://api.github.com/search/users?q=xxxxxx

### 4.4. 消息订阅-发布机制

- 工具库: <font color='red' size='5'>`PubSubJS`</font>
- 下载: <font color='red' size='5'>`npm install pubsub-js --save`</font>
- 使用:
	- `import PubSub from 'pubsub-js'` //引入
	- `PubSub.subscribe('delete', f  unction(data){ });` //订阅
	- `PubSub.publish('delete', data)` //发布消息

### 4.5. 扩展：Fetch

#### 4.5.1. 文档

1.https://github.github.io/fetch/
2.https://segmentfault.com/a/1190000003810652

#### 4.5.2. 特点

- `fetch`: 原生函数，不再使用`XmlHttpRequest`对象提交`ajax`请求
- 老版本浏览器可能不支持

#### 4.5.3. 相关API

1)`GET`请求
```js
fetch(url).then(function(response) {
    return response.json()
}).then(function(data) {
    console.log(data)
}).catch(function(e) {
    console.log(e)
});
```
2)`POST`请求

```js
fetch(url, {
    method: "POST",
    body: JSON.stringify(data),
}).then(function(data) {
    console.log(data)
}).catch(function(e) {
    console.log(e)
})
```

### 第5章：`React`路由

### 5.1. 相关理解

#### 5.1.1 `SPA`的理解

- 单页`Web`应用（single page web application，SPA）。
- 整个应用只有<mark>一个完整的页面</mark>。
- 点击页面中的链接<mark>不会刷新</mark>页面，只会做页面的<mark>局部更新</mark>。
- 数据都需要通过 `ajax` 请求获取, 并在前端异步展现。

#### 5.1.2. 路由的理解

- 什么是路由?
	一个路由就是一个映射关系(`key:value`)
	`key`为路径, `value`可能是`function`或`component`
- 路由分类
	- <mark>后端路由</mark>：
		- 理解： `value`是`function`, 用来处理客户端提交的请求。
		- 注册路由： `router.get(path, function(req, res))`
		- 工作过程：当`node`接收到一个请求时, 根据请求路径找到匹配的路由, 调用路由中的函数来处理请求, 返回响应数据
	- <mark>前端路由</mark>：
		- 浏览器端路由，`value`  是   `component`，用于展示页面内容。
		- 注册路由: 
		- 工作过程：当浏览器的   `path`   变为  `/test` 时, 当前路由组件就会变为  `Test`  组件

```js
<a href="http://www.baidu.com" onclick="return push(' /test1' )">push test1</a> <br> <br>
<button onClick="push('/test2')"> push test2 </button> <br> <br>
<button onClick="replace('/test3')"> replace test3 </button> <br> <br>
<button onClick="back()"> 后退 </button>
<button onClick="forword()"> 前进 </button>

<script type="text/javascript" src="https://cdn.bootcss.com/history/4.7.2/history.js"></script>
<script type="text/javascript">
    // 方法一，直接使用 H5 推出的 history 身上的 API  
	let history = History,createBrowserHistory()
	// 方法二，hash 锚点跳转，兼容性极好
	// let history = History.createHashHistory()
	// 推入
	function push(path){
        history.push(path)
        return false
    }
	// 替换
	function replace(path){
        history.replace(path)
    }
	// 后退
	function back(){
        history.goback()
    }
	// 前进
	function forword(){
        history.goback()
    }
	// 只要路由发生变化就监听 输出
	history.listen((location)=>{
        console.log('请求路由路径变化了', location)
    })
</script>
```

#### 5.1.3. `react-router-dom`  的理解

- `react`的一个插件库。
- 专门用来实现一个`SPA`应用。
- 基于`react`的项目基本都会用到此库。
- 路由器 (router) 管理路由 (route)

### 5.2. `react-router-dom`相关`API`

#### 5.2.1. 内置组件

- `<BrowserRouter>`
- `<HashRouter>`
- `<Route>`
- `<Redirect>`
- `<Link>`
- `<NavLink>`
- `<Switch>`

```jsx
{/* 原生html中，靠 <a>  跳转不同的页面*/}
(/* <a className="list-group-item href="./about.html">About</a>
<a className="list-group-item active" href="./home,html">Home</a> */)

{/* 在 React 中 靠路由链接 实现切换组件 */}
import {Link,BrowserRouter,Route} from 'react-router-dom';
// 
<BrowserRouter>
	<Link className="list-group-item" to="/about"> About </Link>
    <Link className="list-group-item" to="/home"> Home </Link>
</BrowserRouter>
<BrowserRouter>
	<Route path="/about" component={About}/>
</BrowserRouter>
```



#### 5.2.2. 其它

1、`history`对象
2、`match`对象
3、`withRouter`函数

### 5.3. 基本路由使用

#### 5.3.1. 效果

#### 5.3.2. 准备

1.下载  <mark>react-router-dom: npm install --save react-router-dom</mark>
2.引入  `bootstrap.css`: 

##### 一、todoList案例相关知识点

- 1.拆分组件、实现静态组件，注意：className、style的写法
  	
- 2.动态初始化列表，如何确定将数据放在哪个组件的state中？
  - ——某个组件使用：放在其自身的state中
  - ——某些组件使用：放在他们共同的父组件state中（官方称此操作为：状态提升）
    	
- 3.关于父子之间通信：
  - 1.【父组件】给【子组件】传递数据：通过props传递
    			
  - 2.【子组件】给【父组件】传递数据：通过props传递，要求父提前给子传递一个函数
    	
- 4.注意`defaultChecked` 和 `checked`的区别，类似的还有：`defaultValue` 和 `value`
  	
- 5.状态在哪里，操作状态的方法就在哪里

##### 二、`github`搜索案例相关知识点

- 1.设计状态时要考虑全面，例如带有网络请求的组件，要考虑请求失败怎么办。
  	

- 2.`ES6`小知识点：解构赋值+重命名

  ```js
  let obj = {a:{b:1}}
  const {a} = obj; //传统解构赋值
  const {a:{b}} = obj; //连续解构赋值
  const {a:{b:value}} = obj; //连续解构赋值+重命名	
  ```

- 3.消息订阅与发布机制

  - 1.先订阅，再发布（理解：有一种隔空对话的感觉）
    				
  - 2.适用于任意组件间通信
    				
  - 3.要在组件的`componentWillUnmount`中取消订阅
    	

- 4.`fetch`发送请求（关注分离的设计思想）

  ```js
  try {
  	const response= await fetch(`/api1/search/users2?q=${keyWord}`)
  	const data = await response.json()
  	console.log(data);
  } catch (error) {
  	console.log('请求出错',error);
  }
  ```

  


##### 三、路由的基本使用

##### 三、路由组作与一般组件

- 1、写法不同:
  一般组件:`<Demo/>`
  路由组件:`<Route path="/demo"component={Demo}/>`

- 2、存位置不同:
  一般组件:`components`
  路由组件:`pages`

- 3、接收到的`props`不同:
  一般组件:写组件标签时传递了什么，就能收到什么
  路由组件:接收到三个固定的属性

  ```js
  history:
  	go:fgo(n)
  	goBack: fgoBack()
  	goForward:fgoForward()
  	push: fpush(path,state)
  	replace: freplace(path,state)
  location:
  	pathname:"/about"
  	search:""
  	state: undefined
  match:
  	params: {}
  	path:"/about"
  	url:"/about"
  ```

##### 四、NavLink 的使用

```js
{/* 原生html中，靠<a>跳转不同的页面 */}
{/*<a className="list-group-item" href="./about.html">About</a>
<a className="list-group-item active" href="./home.html">Home</a> */}

{/* 在React中靠路由链接实现切换组件--编写路由链接 */}
<NavLink activeClassName="atguigu" className="list-group-item" to="/about"> About </NavLink>
<NavLink activeClassName="atguigu" className="list-group-item" to="/home"> Home </NavLink>
```

##### 五、NavLink与封装NavLink

- 1.`NavLink`可以实现路由链接的高亮，通过`activeClassName`指定样式名
- 2.标签体内容是一个特殊的标签属性
- 3.通过`this.props.children`可以获取标签体内容

```jsx
import React,{Component} from 'react'
import {NavLink,Route} from 'react-router-dom'

export default class MyNavLink extends Component {
    render(){
        const {to,title} = this.props
        return (
            {/*<NavLink activeClassName="atguigu" className="list-group-item" to={to}> {title} </NavLink>*/}
            <NavLink activeClassName="atguigu" className="list-group-item" {...this.props}></NavLink>
        )
    }
}
```

```jsx
// 传递 标签 属性
<MyNavLink to='/about' title='About'>About</MyNavLink>
<MyNavLink to='/home' title='Home'></MyNavLink>

// 传递 标签体 内容
<MyNavLink to='/about'>About</MyNavLink>
<MyNavLink to='/home'>Home</MyNavLink>
```

##### 六、switch的使用

- 1.通常情况下，`path`和`component`是一一对应的关系。

- 2.`Switch`可以提高路由匹配效率(单一匹配)。

  ```jsx
  <Switch>
  	<Route path="/about" component={About}/>
  	<Route path="/home" component={Home}/>
  	<Route path="/home"component={Test}/>
  </Switch>
  ```

##### 七、解决多级路径刷新页面样式系失的问题

- 三种解决办法：
  - 1.`public/index.html`中引入样式时<font color="red">**不写`./`写`/`?**</font>(常用)
  - 2.`public/index.html`中引入样式时不写<font color='red'>**`./`写`%PUBLIC_URL%`**</font >(常用)
  - 3.<font color="red">**使用? HashRouter**</font>   URL #/  后面的都代表是前端资源，不会带给服务器。

##### 八、路由的严格匹配与模糊匹配

- 1.默认使用的是模糊匹配      (简单记:【输入的路径】必须包含要【匹配的路径】，且顺序要一致)
- 2.开启严格匹配:<font color='red'>`<Route exact={true} path="/about"component={About}/>`</font>
- 3.严格匹配不要随便开启，需要再开，有些时候开启会导致无法继续匹配二级路由

```jsx
<Switch>
	<Route exact path="/about" component={About}/>
	<Route exact path="/home" component={Home}/>
	<Route exact path="/home"component={Test}/>
</Switch>
```

##### 九、`Redirect`的使用

- 1.般写在所有路由注册的最下方，当所有路由都无法匹配时，跳转到 `Redirect`指定的路由

- 2.具体编码:

```jsx
<Switch>
	<Route path="/about"component={About}/>
	<Route path="/home"component={Home}/>
	<Redirect to="/about"/>
</Switch>
```

##### 十、嵌套路由

- 1.注册子路由时要写上父路由的path值

- 2.路由的匹配是按照注册路由的顺序进行的



##### 十一、向路由组件传递参数

- 1.`params`参数
  - 路由链接(携带参数)：`<Link to='/demo/test/tom/18'}>详情</Link>`
  - 注册路由(声明接收)：`<Route path="/demo/test/:name/:age" component={Test}/>`
  -  接收参数：this.props.match.params

- 2.`search`参数
  - 路由链接(携带参数)：`<Link to='/demo/test?name=tom&age=18'}>详情</Link>`
  - 注册路由(无需声明，正常注册即可)：`<Route path="/demo/test" component={Test}/>`
  - 接收参数：`this.props.location.search`
  - 备注：获取到的`search`是`urlencoded`编码字符串，需要借助`querystring`解析

- 3.state参数

  - 路由链接(携带参数)：`<Link to={{pathname:'/demo/test',state:{name:'tom',age:18}}}>详情</Link>`

  - 注册路由(无需声明，正常注册即可)：`<Route path="/demo/test" component={Test}/>`
  - 接收参数：`this.props.location.state`
  - 备注：刷新也可以保留住参数

##### 十二、编程式路由导航

- 借助`this.prosp.history`对象上的API对操作路由跳转、前进、后退
  - this.prosp.history.push()
  - this.prosp.history.replace()
  - this.prosp.history.goBack()
  - this.prosp.history.goForward()
  - this.prosp.history.go()

##### 十三、`BrowserRouter` 与 `HashRouter` 的区别

- 1.底层原理不一样：
  - `BrowserRouter`使用的是`H5`的`history API`，不兼容IE9及以下版本。
  -  `HashRouter`使用的是`URL`的哈希值。
-  2.path表现形式不一样
  -  `BrowserRouter`的路径中没有#,例如：`localhost:3000/demo/test`
  - `HashRouter`的路径包含#,例如：`localhost:3000/#/demo/test`

-  3.刷新后对路由state参数的影响
  -  (1).BrowserRouter没有任何影响，因为`state`保存在`history`对象中。
  - (2).`HashRouter`刷新后会导致路由`state`参数的丢失！！！
- 4.备注：`HashRouter`可以用于解决一些路径错误相关的问题。



##### 十四、`antd`的按需引入+自定主题

- 1.安装依赖：`yarn add react-app-rewired customize-cra babel-plugin-import less less-loader`

- 2.修改package.json

```jsx
"scripts": {
    "start": "react-app-rewired start",
    "build": "react-app-rewired build",
    "test": "react-app-rewired test",
    "eject": "react-scripts eject"
},
```

- 3.根目录下创建`config-overrides.js`

  ```js
   //配置具体的修改规则
   const { override, fixBabelImports,addLessLoader} = require('customize-cra');
       module.exports = override(
           fixBabelImports('import', {
             	 libraryName: 'antd',
             	 libraryDirectory: 'es',
               style: true,
           }),
           addLessLoader({
               lessOptions:{
                  javascriptEnabled: true,
                  modifyVars: { '@primary-color': 'green' },
               }
           }),
       );     
  ```

- 4.备注：不用在组件里亲自引入样式了，即：import 'antd/dist/antd.css'应该删掉

### 5.4. 嵌套路由使用

效果

### 5.5. 向路由组件传递参数数据

效果

### 5.6. 多种路由跳转方式

效果



### 第6章：React UI组件库

### 6.1.流行的开源React UI组件库

#### 6.1.1. material-ui(国外)

1.官网: http://www.material-ui.com/#/
2.github: https://github.com/callemall/material-ui

#### 6.1.2. ant-design(国内蚂蚁金服)

1.官网: https://ant.design/index-cn
2.Github: https://github.com/ant-design/ant-design/



### 第7章：redux

### 7.1. redux理解

#### 7.1.1. 学习文档

1.英文文档: https://redux.js.org/
2.中文文档: http://www.redux.org.cn/
3.Github: https://github.com/reactjs/redux

#### 7.1.2. redux是什么

1.redux是一个专门用于做状态管理的JS库(不是react插件库)。
2.它可以用在react, angular, vue等项目中, 但基本与react配合使用。
3.作用: 集中式管理react应用中多个组件共享的状态。

#### 7.1.3. 什么情况下需要使用redux

1.某个组件的状态，需要让其他组件可以随时拿到（共享）。
2.一个组件需要改变另一个组件的状态（通信）。
3.总体原则：能不用就不用, 如果不用比较吃力才考虑使用。

#### 7.1.4. redux工作流程

### 7.2. redux的三个核心概念

#### 7.2.1. action

1.动作的对象
2.包含2个属性
?type：标识属性, 值为字符串, 唯一, 必要属性
?data：数据属性, 值类型任意, 可选属性
3.例子：{ type: 'ADD_STUDENT',data:{name: 'tom',age:18} }

#### 7.2.2. reducer

1.用于初始化状态、加工状态。
2.加工时，根据旧的state和action， 产生新的state的纯函数。

#### 7.2.3. store

1.将state、action、reducer联系在一起的对象
2.如何得到此对象?
1)import {createStore} from 'redux'
2)import reducer from './reducers'
3)const store = createStore(reducer)
3.此对象的功能?
1)getState(): 得到state
2)dispatch(action): 分发action, 触发reducer调用, 产生新的state
3)subscribe(listener): 注册监听, 当产生了新的state时, 自动调用

### 7.3. redux的核心API

#### 7.3.1. createstore()

作用：创建包含指定reducer的store对象

#### 7.3.2. store对象

1.作用: redux库最核心的管理对象
2.它内部维护着:
1)state
2)reducer
3.核心方法:
1)getState()
2)dispatch(action)
3)subscribe(listener)
4.具体编码:
1)store.getState()
2)store.dispatch({type:'INCREMENT', number})
3)store.subscribe(render)

#### 7.3.3. applyMiddleware()

作用：应用上基于redux的中间件(插件库)

#### 7.3.4. combineReducers()

作用：合并多个reducer函数

### 7.4. 使用redux编写应用

效果

### 7.5. redux异步编程

#### 7.5.1理解：

1.redux默认是不能进行异步处理的,
2.某些时候应用中需要在redux中执行异步任务(ajax, 定时器)

#### 7.5.2. 使用异步中间件

npm install --save redux-thunk

### 7.6. react-redux

#### 7.6.1. 理解

1.一个react插件库
2.专门用来简化react应用中使用redux

#### 7.6.2. react-Redux将所有组件分成两大类

1.UI组件
1)只负责 UI 的呈现，不带有任何业务逻辑
2)通过props接收数据(一般数据和函数)
3)不使用任何 Redux 的 API
4)一般保存在components文件夹下
2.容器组件
1)负责管理数据和业务逻辑，不负责UI的呈现
2)使用 Redux 的 API
3)一般保存在containers文件夹下

#### 7.6.3. 相关API

1.Provider：让所有组件都可以得到state数据

2.connect：用于包装 UI 组件生成容器组件

3.mapStateToprops：将外部的数据（即state对象）转换为UI组件的标签属性

4.mapDispatchToProps：将分发action的函数转换为UI组件的标签属性

### 7.7. 使用上redux调试工具

#### 7.7.1. 安装chrome浏览器插件

#### 7.7.2. 下载工具依赖包

npm install --save-dev redux-devtools-extension

### 7.8. 纯函数和高阶函数

#### 7.8.1. 纯函数

1.一类特别的函数: 只要是同样的输入(实参)，必定得到同样的输出(返回)
2.必须遵守以下一些约束  
1)不得改写参数数据
2)不会产生任何副作用，例如网络请求，输入和输出设备
3)不能调用Date.now()或者Math.random()等不纯的方法  
3.redux的reducer函数必须是一个纯函数

#### 7.8.2. 高阶函数

1.理解: 一类特别的函数
1)情况1: 参数是函数
2)情况2: 返回是函数
2.常见的高阶函数:
1)定时器设置函数
2)数组的forEach()/map()/filter()/reduce()/find()/bind()
3)promise
4)react-redux中的connect函数
3.作用: 能实现更加动态, 更加可扩展的功能

## 1. setState

### setState更新状态的2种写法

```
	(1). setState(stateChange, [callback])------对象式的setState
            1.stateChange为状态改变对象(该对象可以体现出状态的更改)
            2.callback是可选的回调函数, 它在状态更新完毕、界面也更新后(render调用后)才被调用
					
	(2). setState(updater, [callback])------函数式的setState
            1.updater为返回stateChange对象的函数。
            2.updater可以接收到state和props。
            4.callback是可选的回调函数, 它在状态更新、界面也更新后(render调用后)才被调用。
总结:
		1.对象式的setState是函数式的setState的简写方式(语法糖)
		2.使用原则：
				(1).如果新状态不依赖于原状态 ===> 使用对象方式
				(2).如果新状态依赖于原状态 ===> 使用函数方式
				(3).如果需要在setState()执行后获取最新的状态数据, 
					要在第二个callback函数中读取
```



------



## 2. lazyLoad

### 路由组件的lazyLoad

```jsx
	//1.通过React的lazy函数配合import()函数动态加载路由组件 ===> 路由组件代码会被分开打包
	const Login = lazy(()=>import('@/pages/Login'))
	
	//2.通过<Suspense>指定在加载得到路由打包文件前显示一个自定义loading界面
	<Suspense fallback={<h1>loading.....</h1>}>
        <Switch>
            <Route path="/xxx" component={Xxxx}/>
            <Redirect to="/login"/>
        </Switch>
    </Suspense>
```



------



## 3. Hooks

#### 1. React Hook/Hooks是什么?

- (1). Hook是React 16.8.0版本增加的新特性/新语法
- (2). 可以让你在函数组件中使用 state 以及其他的 React 特性

#### 2. 三个常用的Hook

- (1). State Hook: `React.useState()`
- (2). Effect Hook: `React.useEffect()`
- (3). Ref Hook: `React.useRef()`

#### 3. State Hook

- (1). `State Hook`让函数组件也可以有state状态, 并进行状态数据的读写操作
- (2). 语法: `const [xxx, setXxx] = React.useState(initValue)  `
- (3). `useState()`说明:
  - 参数: 第一次初始化指定的值在内部作缓存   
  - 返回值: 包含2个元素的数组, 第1个为内部当前状态值, 第2个为更新状态值的函数
- (4). `setXxx()`2种写法:
  - `setXxx(newValue)`: 参数为非函数值, 直接指定新的状态值, 内部用其覆盖原来的状态值
  - ` setXxx(value => newValue)`: 参数为函数, 接收原本的状态值, 返回新的状态值, 内部用其覆盖原来的状态值

#### 4. Effect Hook

- (1). Effect Hook 可以让你在函数组件中执行副作用操作(用于模拟类组件中的生命周期钩子)
- (2). React中的副作用操作:
          发ajax请求数据获取
          设置订阅 / 启动定时器
          手动更改真实DOM
- (3). 语法和说明: 
          useEffect(() => { 
            // 在此可以执行任何带副作用操作
            return () => { // 在组件卸载前执行
              // 在此做一些收尾工作, 比如清除定时器/取消订阅等
            }
          }, [stateValue]) // 如果指定的是[], 回调函数只会在第一次render()后执行
- (4). 可以把 useEffect Hook 看做如下三个函数的组合
          `componentDidMount()`
          `componentDidUpdate()`
      	`componentWillUnmount() `

#### 5. Ref Hook

- (1). `Ref Hook`可以在函数组件中存储/查找组件内的标签或任意其它数据
- (2). 语法: `const refContainer = useRef()`
- (3). 作用:保存标签对象,功能与`React.createRef()`一样



------



## 4. Fragment

### 使用

	`<Fragment><Fragment>`
	`<></>`

### 作用

> 可以不用必须有一个真实的DOM根标签了



<hr/>

## 5. Context

### 理解

> 一种组件间通信方式, 常用于【祖组件】与【后代组件】间通信

### 使用

```js
1) 创建Context容器对象：
	const XxxContext = React.createContext()  
	
2) 渲染子组时，外面包裹xxxContext.Provider, 通过value属性给后代组件传递数据：
	<xxxContext.Provider value={数据}>
		子组件
    </xxxContext.Provider>
    
3) 后代组件读取数据：

	//第一种方式:仅适用于类组件 
	  static contextType = xxxContext  // 声明接收context
	  this.context // 读取context中的value数据
	  
	//第二种方式: 函数组件与类组件都可以
	  <xxxContext.Consumer>
	    {
	      value => ( // value就是context中的value数据
	        要显示的内容
	      )
	    }
	  </xxxContext.Consumer>
```

### 注意

	在应用开发中一般不用context, 一般都它的封装react插件



<hr/>


## 6. 组件优化

### Component的2个问题 

- 只要执行`setState()`,即使不改变状态数据, 组件也会重新`render()`

- 只当前组件重新`render()`, 就会自动重新`render`子组件 ==> 效率低

### 效率高的做法

- 只有当组件的`state`或`props`数据发生改变时才重新`render()`

### 原因

- `Component`中的`shouldComponentUpdate()`总是返回`true`

### 解决

- 办法1: 
  	重写`shouldComponentUpdate()`方法
  	比较新旧state或props数据, 如果有变化才返回true, 如果没有返回false
- 办法2:  
  	使用`PureComponent`
  	`PureComponent`重写了`shouldComponentUpdate()`, 只有`state`或`props`数据有变化才返回`true`
  	
- 注意: 
  		只是进行`state`和props数据的浅比较, 如果只是数据对象内部数据变了, 返回false  
  		不要直接修改state数据, 而是要产生新数据
  项目中一般使用`PureComponent`来优化


## 7. render props

### 如何向组件内部动态传入带内容的结构(标签)?

	Vue中: 
		使用slot技术, 也就是通过组件标签体传入结构  <AA><BB/></AA>
	React中:
		使用children props: 通过组件标签体传入结构
		使用render props: 通过组件标签属性传入结构, 一般用render函数属性

### children props

	<A>
	  <B>xxxx</B>
	</A>
	{this.props.children}
	问题: 如果B组件需要A组件内的数据, ==> 做不到 

### render props

	<A render={(data) => <C data={data}></C>}></A>
	A组件: {this.props.render(内部state数据)}
	C组件: 读取A组件传入的数据显示 {this.props.data} 



<hr/>

## 8. 错误边界

#### 理解：

错误边界：用来捕获后代组件错误，渲染出备用页面

#### 特点：

只能捕获后代组件生命周期产生的错误，不能捕获自己组件产生的错误和其他组件在合成事件、定时器中产生的错误

##### 使用方式：

​	`getDerivedStateFromError`	配合	`componentDidCatch`

```js
// 生命周期函数，一旦后台组件报错，就会触发
static getDerivedStateFromError(error) {
    console.log(error);
    // 在render之前触发
    // 返回新的state
    return {
        hasError: true,
    };
}

componentDidCatch(error, info) {
    // 统计页面的错误。发送请求发送到后台去
    console.log(error, info);
}
```

## 9. 组件通信方式总结

#### 方式：

- props：
  - (1).children props
  - (2).render props
- 消息订阅-发布：
  - pubs-sub、event等等
- 集中式管理：
  - `redux`、`dva`等等
- `conText`:
  - 生产者-消费者模式

#### 组件间的关系

- 父子组件：props
  	
- 兄弟组件(非嵌套组件)：消息订阅-发布、集中式管理
  	
- 祖孙组件(跨级组件)：消息订阅-发布、集中式管理、conText(用的少)

