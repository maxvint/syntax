##__编码规范__
文件编码统一为：__UTF-8__，请开发人员调整编辑器的文件编码为UTF-8，并关闭UTF-8 BOM的功能。请不要使用windows自带的记事本编辑项目文件。

##__命名规范__
####类命名
使用__大驼峰法__命名，即每个单词的首字母均大写；

	class SimpleDB {

	}

####函数命名
使用__小驼峰法__命名，即第一个单词首字母小写，其余单词首字母均大写；
	
	public function __construct($downloadPath = '') {

	}

####变量命名
使用__小驼峰法__命名，即第一个单词首字母小写，其余单词首字母均大写；

	protected $callbackFunctions;

如为私有变量，请在变量名前方加上下划线。

	private $_adapter;

####常量命名
所有字母均大写，前后加上双下划线，单词之间用下划线分割；如果为ThinkSNS内部常量，则使用tsdefine();
	
	define('SITE_PATH', dirname(__FILE__));
	tsdefine('IS_HTTPS', 0);



##__注释规范__
####文件头部注释
文件头部注释主要用来阐述此文件的作用，作者，版本。按照以下形式书写：

	<?php
	/**
	 * 用户认证模型 - 数据对象模型
	 * @author Yuwenhui <yuwenhui1986@gmail.com>
	 * @version $Id$
	 */

其中@author为作者的名称，后面<>中为电子邮箱；@version定义为$Id$是为了匹配svn的关键字。

####引用文件和定义常量注释
文件的引用和常量的定义一般都放置在文件的开头部分。采用双斜线注释法(//)。
	
	// 定义MySQL查询输出封装为多结果，必须用循环处理
	define('CLIENT_MULTI_RESULTS', 131072);

	// 加载上传操作类
	require_once SITE_PATH.'/addons/library/UploadFile.class.php';

多行注释，使用如下形式：
	
	/**
	 * Cookie 设置、获取、清除 (支持数组或对象直接设置) 2009-07-9
	 * 1 获取cookie: cookie('name')
	 * 2 清空当前设置前缀的所有cookie: cookie(null)
	 * 3 删除指定前缀所有cookie: cookie(null,'think_') | 注：前缀将不区分大小写
	 * 4 设置cookie: cookie('name','value') | 指定保存时间: cookie('name','value',3600)
	 * 5 删除cookie: cookie('name',null)
	 * $option 可用设置prefix,expire,path,domain
	 * 支持数组形式:cookie('name','value',array('expire'=>1,'prefix'=>'think_'))
	 * 支持query形式字符串:cookie('name','value','prefix=tp_&expire=10000')
	 * 2010-1-17 去掉自动序列化操作，兼容其他语言程序。
	 */

####类(接口)注释
一个类(接口)在声明的时候必须声明其作用。

	/**
	 * 功能升级类
	 * 功能1：
	 * 功能2：
	 * @author 水上铁 <476974493@qq.com>
	 * @version $Id$
	 */
	class Image {

	}

注释第一行声明类的作用，后面为类实现的主要功能；@author为作者的名称，后面<>中为电子邮箱；@version定义为$Id$是为了匹配svn的关键字。

####函数注释
函数的注释包括函数作用、参数和返回值。注意如果是无返回的函数，必须指明@return void。

	/**
	 * 获取语言配置内容列表
	 * @param array $map 查询条件
	 * @return array 语言配置内容列表
	 */
	public function getLangContent($map) {

	}

	/**
	 * 更改语言配置内容
	 * @param array $data 语言配置内容
	 * @param integer $sid 语言资源ID
	 * @return integer 是否更改成功，1表示成功；0表示失败
	 */
	public function updateLangData($data, $sid) {

	}
	

注释第一行声明函数的作用；@param指函数的参数；@return是函数的返回值。

####程序行间注释
行间注释采用双斜线注释法

	// 更新缓存文件
 	$this->createCacheFile($addData['appname'], $addData['filetype']);

##__书写规范__
####对齐和缩进
每个缩进的单位约定是一个TAB(4个空白字符宽度，而不是4个空格)，请每个开发人员在编辑器(UltraEdit、EditPlus、Eclipse、Sublime Text等)中进行强制设定，以防在编写代码时遗忘而造成格式上的不规范。

####大括号{}、if和switch
首括号 { 与关键词同行，尾括号 } 与关键字同列；

	if($condition) {
		switch($var) {
			case 1: echo 'var is 1'; break;
			case 2: echo 'var is 2'; break;
			default: echo 'var is neither 1 or 2'; break;
		}
	}

if结构中，else和elseif与前后两个大括号同行，左右各一个空格。另外，即便if后只有一行语句，仍然需要加入大括号，以保证结构清晰；

	if($condition) {
		$var++;
	} else {
		$var--;
	}

switch结构中，通常当一个case块处理后，将跳过之后的case块处理，因此大多数情况下需要添加break。break的位置视程序逻辑，与case同在一行，或新起一行均可，但同一switch体中，break的位置格式应当保持一致。
	
	if($condition) {
		switch($var) {
			case 1: echo 'var is 1'; break;
			case 2: echo 'var is 2'; break;
			default: echo 'var is neither 1 or 2'; break;
		}
	} else {
		switch($str) {
			case 'abc':
				$result = 'abc';
				break;
			default:
				$result = 'unknown';
				break;
		}
	}

####运算符、小括号、关键词和函数
每个运算符与两边参与运算的值或表达式中间要有一个空格，唯一的特例是字符连接运算符号 . 两边不加空格；
	
	$result = (($a + 1) * 3 / 2 + $num)).'Test';
	$condition ? func1($var) : func2($var);

左括号 ( 应和函数关键词紧贴在一起；右括号 ) 除后面是 ) 或者 . 以外，其他一律用空格隔开它们；
	
	function fun1($var1, $var2) {

	}

	exit(json_encode($data));

每段较大的程序体，上、下应当加入空白行，两个程序块之间只使用1个空行，禁止使用多行。少于15行的程序块，可不加上下空白行。

####函数的缩进
函数参数的命名和变量的命名规范一致；
函数定义中的左小括号 ( ，与函数名紧挨，中间无需空格；
开始的左大括号与函数定义为同一行，中间加一个空格，不要另起一行；
具有默认值的参数应该位于参数列表的后面；
函数调用与定义的时候参数与参数之间加入一个空格；
必须仔细检查并切实杜绝函数起始缩进位置与结束缩进位置不同的现象；
符合规范的定义：
	
	public function index($string, $operation, $key = '') {
		//函数体
	}

不符合规范的定义：

	public function authcode ($string,$key='',$operation)
	{
		//函数体
	}

####引号
PHP中单引号和双引号具有不同的含义，最大的几项区别如下：  
单引号中，任何变量($var)、特殊转义字符(如 \t \r \n 等)不会被解析，因此PHP的解析速度更快，转义字符仅仅支持 \' 和 \\ 这样对单引号和反斜杠本身的转义；  
双引号中，变量($var)值会代入字符串中，特殊转义字符也会被解析成特定的单个字符，这样虽然程序编写更加方便，但同时PHP的解析也很慢；  
数组中，如果下标不是整型，而是字符串类型，请务必用单引号将下标括起，正确的写法为$array['key']，而不是$array[key]；因为不正确的写法会使PHP解析器认为key是一个常量，进而先判断常量是否存在，不存在时才以 key 作为下标带入表达式中，同时出发错误事件，产生一条Notice级错误。

因此，在绝大多数可以使用单引号的场合，禁止使用双引号。依据上述分析，可以或必须使用单引号的情况包括但不限于下述：

* 字符串为固定值，不包含 `\t` 等特殊转义字符；
* 数组的固定下标，例如：`$array['key'];`；
* 表达式中不需要带入变量，例如：`$string = 'test';`， 而非：`$string = "test$var";`；
* 数据库SQL语句中，所有数据必须加单引号，无论数值还是字串，以避免可能的注入漏洞和SQL错误。