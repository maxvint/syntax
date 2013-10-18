# Javascript编码规范

## 命名规范
#### 通用命名规则
* 所有变量必须是有意义的英文，严厉禁止拼音；
* 变量命名采用小驼峰法(第一个单词首字母小写，其余单词首字母大写)；
* 变量允许使用公认英文缩写，例如`nav`；
* 常量必须所有单词大写，并且每个单词间加下划线；
* 类命名必须是大驼峰法(所有单词第一个字母均大写)；
* 私有类的变量属性成员， 建议使用混合式命名，并前面下下划线；
* "on"只能用作事件的命名；
* 所有全局变量必须初始化；
* 保留字以及特有的dom属性不能作为变量名。

#### 变量命名规范
类型前缀 + 有意义的单词

* 字符串：sXXX，如：sName，sHtml；
* 数字：nXXX，如：nPage，nTotal；
* 逻辑：bXXX，如：bChecked，bHasLogin；
* 数组：aXXX，如：aList，aGroup；
* 正则：rXXX，如：rDomain，rEmail；
* 函数：fXXX，如：fGetList；
* DOM节点：dXX，如：dDiv，dSpan；
* 其他类型：oXXX，如：oButton，oDate；
* 特殊简写：小范围作用域临时变量，如函数内部的局部变量或参数：o(Object)、e(Element)、evt(event)、err(errot)等；
* 循环变量：i、j、k以此类推；

#### 函数命名规范
* 普通函数：动词+名词，如：fGetList、fGetVersion；
* 涉及逻辑返回值的函数：is、has、can，如：fisAdmin、fhasChild；
* 内部函数：_f+上面规则，如：fLoopCount；

## 书写规范
#### 对齐和缩进
* 必须使用 Tab 键进行代码缩进，以节约代码大小，建议设置编辑器的tab为4个空格的宽度（而不是4个空格）；
* 所有语句结束后，必须使用 ; 号结束；
* 大括号前面不能换行；
* 操作符必须使用空格隔开；

#### 语法结构
普通代码段应该如下：

	while(!isDone) {
		doSomething();
		isDone = moreToDo();
	}

变量定义方法如下：

	var a = null;
	var b = 1;
	var c = 0;

函数定义方法如下：

	var funcA = function() {
		var a = 0;
		...
	}

if 语句应该像这样：

	if(someCondition) {
		statements;
	} else if(someOtherCondition) {
		statements;
	} else {
		statements;
	}

for 语句应该像这样：

	for(initialization; condition; update) {
		statements;
	}

while 语句应该像这样：

	while(!isDone) {
		doSomething();
		isDone = moreToDo();
	}

do ... while 语句应该像这样：

	do {
		statements;
	} while(condition);

switch 语句应该像这样：
	
	switch(condition) {
		case "A": 
			statements;		//注释
			break;
		case "B": 
			statements;
			break;
		default:
			statements;
			break;
	}

try ... catch 语句应该像这样：
	
	try {
		statements;
	} catch(ex) {
		statements;
	} finally {
		statements;
	}

单行的 if - else，while 或者 for 语句也必须加入括号：

	if(condition) {
		statement;
	}
	
	while(condition) {
		statement;
	}

	for(intialization; condition; update) {
		statement;
	}

## Javascript编写风格
#### 对象定义规范
在Javascript中，所有类型都是对象，包括string类型。函数的定义，统一使用以下方式：

	var a = function() {...};

最后要加上 “;”号，不要再使用以下方式：

	function a() {}

对象定义规范：

* string类型定义：`var str = 'xxxxxx';`
* function类型定义：`var func = function() {...};`
* array类型定义：`var arr = new Array();`
* object类型定义：`var obj = {'name': 'xxxxxx', 'age': '10'}`

#### 事件监听
开发中统一使用module.js对对象事件(DOM节点)进行监听。

__块状节点：__model-node，包括的标签：div、ul、li、dl、form等，例如：

	<div model-node="testmodel" model-args="name=testname&value=testvalue"></div>

__独立事件节点：__event-node，包括的标签：a、span、label、strong、input、select、button、img、textarea、h1、h2、h3、h4、i等，例如：

	<a href="javascript:void(0);" event-node="testevent" event-args="name=testname&value=testvalue"></a>

__事件监听方法：__load、click、mouseenter、mouseleave