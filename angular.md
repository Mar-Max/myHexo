---
title: Angular学习笔记
---

# Angular 学习笔记


### 一、概述

AngularJS 是比较新的技术，版本 1.0 是在 2012 年发布的。

AngularJS 是由 Google 的员工 Miško Hevery 从 2009 年开始着手开发。

这是一个非常好的构想，该项目目前已由 Google 正式支持，有一个全职的开发团队继续开发和维护这个库。


### 二、angular的指令系统

+ ng-app:初始化一个 AngularJS 应用程序
+ ng-controller：指令定义了应用程序控制器


### 三、angular的双向数据绑定

+ MVVM：双向绑定模式
+ $timeout：angular自带定时器
+ ng-click：指令定义了 AngularJS 点击事件
+ ng-model：双向绑定功能
    

### 四、angular的模块化

+ angular.module：模块化一个angular
+ 压缩代码写法：m.controller('name',['$scope',function(s){}]);


### 五、angular的工具方法

  + angular.bind:修改方法this指向
  + angular.copy:复制模块
  + angular.extend:继承模块
  + angular.isArray:检测是否为字符串
  + angular.isDate:检测是否为时间对象
  + angular.isDefined:检测是否定义
  + angular.isUndefined:检测是否未定义
  + angular.isFunction:检测是否为函数
  + angular.isNumber:检测是否为数字
  + angular.isObject:检测是否为对象
  + angular.isString:检测是否为字符串
  + angular.isElement:检测是否为DOM对象
  + angular.version:显示angular版本
  + angular.equals:判断是否相等（数组对象可相等、NaN可相等）  
    - angular.equals(a,b) => Boolen`
  + angular.forEach:循环
    - angular.forEach(循环对象,回调函数(value,name),结果(this指向))
  + angular.fromJson/toJson：字符串解析为对象/对象解析为字符串    
  + angular.identity/noop:返回参数自身/返回undefined
  + angular.lowercase/uppercase:转换为小写/转换为大写
  + angular.element:获取元素
  + angular.bootstrap:动态初始化angular
  	- 动态添加ng-app
  	- 多个模块初始化
  + angular.injector:内部使用方法
  

### 六、$scope下的常用方法

+ $scope.$watch:监听指定对象

	```js
	//$.scope.$watch(监听对象，回调(新值，旧值)，是否实时监听)
	$scope.$watch($scope.sum,function(newVal,oldVal){
		$scope.apple.fre = newVal >= 100 ? 0 : 10;
	},true);
	```

+ $scope.$apply:可以监听数据是否变化从而影响视图（可以支持原生js方法内使用）

	```js
  	setTimeout(function(){
  		$scope.$apply(function(){
  			$scope.name = '你好！';
  		});
  	},1000);
	```


### 七、angular.module下常用方法

+ controller:初始化控制器

 ```js
  	angular.module('mod',[]).controller(['$scope'],function($scope){});
 ```
 
+ run:初始化全局作用域下方法属性

 ```js
  	angular.module('mod',[]).run(['$rootScope'],function($rootScope){});
 ```
  	
### 八、angular的过滤器
+ currency:转换为货币

  `{{num | currency:货币符号:第二参数:第三参数}}`

+ number:转化为格式化数字

  `{{num | number:保留位数}}`

+ lowercase/uppercase:小写/大写转换

  `{{str | lowercase}}`

  `{{str | uppercase}}`

+ json:格式化json

  `{{json | json}}`

+ limitTo:截取字符串/数组

  `{{str | limitTo:截取位数}}`

  `{{arr | limitTo:截取数量}}`

+ date:格式化时间

  `{{time | date:日期格式}}`

+ orderBy:数据排序

  `{{data | orderBy:排序关键字(key):反向排序(Boolean)}}`

+ filter:数据过滤

  `{{data | filter:过滤关键字(value):严格匹配(Boolean)}}`


### 九、过滤器扩展
+ 可组合使用过滤器:

	`{{str | limitTo:2 | uppercase}}`

+ js中使用过滤器
  - 过滤器服务:$filter;
  
  	*控制器中需要引入，功能等同于插值表达式中`{{操作对象| 服务名:服务参数}}`写法。*
  
	`$filter(服务名)(操作对象,服务参数)；`
  
  
+ 自定义过滤器
    - angular.module('mod',[]).filter();
    
    ```js
    m.filter(过滤器名,function(){
    	return function(操作对象,过滤器参数){
    		//code
    		return 处理结果；
    	}
    });
    ```


### 十、ng-repeat指令
- 遍历集合

  `ng-repeat = "name in data"`
  
- 扩展
  + $index:输出索引值
  + $first:判断是否为第一元素
  + $middle:判断是否为中间元素(除首尾元素外)
  + $last:判断是否为最后元素
  + $event:判断是否为偶数行
  + $odd:判断是否为奇数行
  
    `<li class="{{$even ? 'even' : 'odd'}}"></li>`
  
- 块循环遍历
  + ng-repeat-start
  + ng-repeat-end
 
  	```html
  	<div ng-repeat-start="name in data">{{$index}}</div>
 	<p>{{name}}</p>
  	<div ng-repeat-end>{{name}}</div>
    ```


### 十一、事件指令

+ ng-click/dblclick:鼠标点击/双击事件
+ ng-mousedown/mouseup:鼠标按下/抬起事件
+ ng-mouseover/mouseout:鼠标移入/移出事件
+ ng-mouseenter/mouseleave:鼠标移入/移出事件
+ ng-mousemove:鼠标移动事件
+ ng-keydown/keyup/keypress:键盘按下/抬起/输入事件
+ ng-focus/blur: 获取焦点/失去焦点事件
+ ng-submit: 提交事件
+ ng-selected:下拉菜单选择事件
+ ng-change:输入框改变事件
+ ng-copy:拷贝事件
+ ng-cut:剪切事件
+ ng-paste:粘贴事件


### 十二、angular的指令

**1.input相关指令**

+ ng-disabled:禁用指令
  - 服务:$interval:定时器
  - 清除定时器:$interval.cancel(timer);
+ ng-readonly:text输入框只读指令
+ ng-checked:checkbox选中指令
+ ng-value:替代value(优势:不会看到插值表达式原形)

**2.数据显示处理**

+ ng-bind:类似ng-value，可用于常规标签中

  `<div ng-bind="text"></div> <=> <div>{{text}}</div>`

+ ng-cloak:angular解析完毕显示
  
  `<div ng-cloak>{{text}}</div>`

+ ng-bind-template:支持多表达式

  `<div ng-bind-template="{{text}},{{text}}"></div>`
  
+ ng-bind-html:支持html格式字符串转为正常html格式(需要angular-sanitize插件)
  
  ```html
  <!-- $scope.tpl = "<h1>标题</h1>"; -->
  <div ng-bind-html="tpl"></div>
  ```

+ ng-non-bindable:不解析插值表达式

**3.属性相关指令**

+ ng-class:操作class

  `<div ng-class="{classA:true,classB:true}"></div>`

+ ng-style:操作style样式(value值必须带引号)

  `<div ng-style="{color:'#fff',background:'#cc0'}">{{text}}</div>`

+ ng-href:操作href

  `<a ng-href="{{href}}">{{text}}</a>`

+ ng-src:操作src

  `<img ng-src="{{src}}">`

+ ng-attr-(suffix):通用属性操作

  `<a ng-attr-href="{{href}}" ng-attr-title="{{text}}" ng-attr-id="{{text}}">{{text}}</a>`
  
**4.dom操作指令**

+ ng-show:元素显示/隐藏
+ ng-hide:元素隐藏/显示
+ ng-if:添加/删除节点
+ ng-switch:有选择的显示/隐藏切换
  - on:关联布尔值
  - ng-switch-default:默认显示
  - ng-swithc-when:切换显示
  
  ```html
    <div ng-switch on="bBtn">
		<p ng-switch-default>默认效果</p>
		<p ng-switch-when="false">切换效果</p>
	</div>
  ```  
  
+ ng-open:控制details标签展开/收起(details标签只有webkit内核浏览器支持)

**5.指令扩展部分**

+ ng-init:初始化数据
+ ng-include:通过模板方式引入(需要服务器环境)

  `<div ng-controller="ctrl" ng-include="'temp.tpl'"></div>`

+ ng-model:双向绑定
  - ng-model-options:更新视图数据设置
  - updateOn:触发指定事件时更新视图
  
  `<input type="text" ng-model="text" ng-model-options="{updateOn:'blur'}">`

+ ng-controller:控制器
  - as:控制器回调函数为构造函数时，使用as访问对象值
  
**6.常用标签指令:控制器内的标签(没有默认行为)**

+ `<a>`
+ `<select>`:需要配合ng-model
  - ng-options
  
  ```html
    <select ng-options=" list.name for list in data " ng-model="myData">
	</select>
  ```
  
+ `<textarea>`
+ `<input>`
+ `<form>`
  - novalidate:阻止表单默认行为样式
  
  ```html
    <form novalidata>
		<input type="email">
	</form>
  ```


### 十三、表单验证指令(通过name验证)

+ $valid:表单验证通过(有效)时为true，失败(无效)为false(与$invalid相反)
+ $invalid:表单验证失败(无效)时为true，通过(有效)时为true(与$valid相反)
+ $pristine:验证值未被修改时为true,修改时为false(与$dirty相反)
+ $dirty:验证值被修改时为ture,未被修改时为false(与$pristine相反)
+ $error:验证失败/通过

  ```html
    <!-- $scope.str = 'hello world!'; -->
    <form novalidata name="myForm">
		<input type="email" name="myText" ng-model="str">
		<div>{{myForm.myText.$valid}}</div>
		<div>{{myForm.myText.$invalid}}</div>
		<div>{{myForm.myText.$pristine}}</div>
		<div>{{myForm.myText.$dirty}}</div>
		<div>{{myForm.myText.$error}}</div>
    </form>
  ```
  

### 十四、自定义指令
  
#### m.directive()

- restrict:指令类型，可组合使用
  + E:元素(Element)指令
  + A:属性(Attribute)指令
  + C:样式(ClassName)指令
  + M:注释指令
- replace:是否替换容器标签
- template:自定义模板
- templateUrl:指定外部模板(需要服务器环境)
- transclude:是否可嵌套(ng-transclude指引嵌套位置)
- scope:是否设置独立作用域
  + 独立作用域:true
  + 隔离作用域:{}
  
    **绑定策略：**
    
    - @:绑定解析值
    - =:绑定解析数据
    - &:绑定解析函数
- controller:内部控制器(指令与指令交互)
- require:引入其他指令
  + ^ : 父级
  + ? : 容错处理
- link:对当前元素进行dom操作
  + scope:作用域
  + element:模板父级元素
  + attr:当前模板属性
  + reController:引入的控制器


  ```js
	//指令名称(驼峰命名,不能大写开头)
	m.directive('myList',function(){
		return {
			restrict : 'E',
			replace : true,
			transclude : true,
			scope : {
			  myId : '@',
			  myName : '=',
			  myFn : '&'
			},
			controller : ['$scope',function($scope){
			    this.name = 'Mr.Ma';
			}],
			template : '<div id={{myId}} ng-click="myFn({num:123})">{{text}}<h1 ng-transclude></h1></div>'
		};
	});

	m.directive('hi',function(){
		return {
			restrict : 'E',
			require : '^?myList',
			template : '<span>你好！</span>',
			link : function(scope,element,attr,reController){
			    console.log(reController.name); //=> ’Mr.Ma‘
			}    
		}
	});

	m.controller(['$scope'],function($scope){
		$scope.text = "hello world";
	});
  ```

  ```html
    <div ng-controller="ctrl">
        <my-list my-id="divA" my-name="text"  my-fn="show(num)">
            <hi></hi>
            </my-list>
          <my-list my-id="divB" my-name="text" my-fn="show(num)"></my-list>
    </div>
  ```

  
### 十五、angular的服务

+ $scope:模块作用域
  - $watch:监听
  - $apply:原生JS下监听修改数据
+ $rootScope:全局作用域
+ $timeout:单次定时器
+ $interval:循环定时器
+ $filter:过滤器
+ $http:类似ajax功能
  - method:请求方式(jsonp方式请求回调名需写为'JSON_CALLBACK')
  - url:请求地址
  - success:请求成功
  - error:请求失败
  
    ```js
        $http({
	        method : 'GET',
	        url : 'data.php'
	    }).success(function(data,state,headers,config){
	        console.log(data,state,headers,config);
	    }).error(function(err){
	        console.log(err);
	    });
     ```
  
  **简写方式：**
  
     ```js
        $http.get('data.php').success(function(data){
            console.log(data);
        }).error(function(err){
           console.log(err);
        });
     ```
  
+ $location:网址信息
  - absUrl():网址绝对地址(编码后地址)
  - path():路由地址(#/号后面地址)
    + 获取路由地址:`$location.paht()`
    + 设置路由地址:`$location.path(/路由A/路由B)`
  - replace():取消历史记录功能
  
    `$location.path().replace()`
  
  - hash():哈希值(#号后面的地址)
    + 获取哈希值:`$location.hash()`    
    + 设置哈希值:`$location.hash('hello')`
  - search():设置数据值
    + 获取数据值:`$location.search()`
    + 设置数据值:`$location.search({'cb':'JSON_CALLBACK'})`
  
  - url():获取网址信息(path+hash+search)
  - host():获取主机名`127.0.0.1`
  - port():获取端口号`8080`
  - protocol():获取协议名`http`
+ $anchorScroll:锚点跳转功能

  - 重新执行锚点功能:`$anchorScroll()`

+ $cacheFactory:
  - info():
  - put():
  - get():
  - remove():
  




















