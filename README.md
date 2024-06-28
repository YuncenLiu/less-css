### less

less 是一种动态样式语言，属于CSS预处理器的范围，它扩展了css 语言，它扩展了 css 语言，增加了变量，minx，函数等特性，使css更易维护和扩展

[less 中文官网](https://lesscss.cn/)

[bootstrap 中文 less 官网](https://www.bootcss.com/p/lesscss/)


#### less编译工具

VSCode Easy LESS`v2.0.0`

#### less注释

1. `//` 这种注释会被编译到 css 文件
2. `/**/` 这种注释不会被编译到 css 文件

#### 变量

使用 @ 来申明一个变量、属性名、值

```less
@color:pink;
@m:padding;
@selector:#wrap;

@{selector} {
	@{m}: 0;
	background-color: @color;
}
```

变量的延迟加载

```less
@var: 0;
.class {
    @var: 1;
    .barss {
        @var: 2;
        three: @var;
        @var: 3;
    }
    one: @var;
}
```

转化后会变成

```css
.class {
  one: 1;
}
.class .barss {
  three: 3;
}
```

#### 嵌套规则

1. 基本嵌套规则
2.  `&` 嵌套规则 平级，删除空格


#### 混合

混合就是讲一系列属性从一个规则集引入到另外一个规则集

1. 普通混合：混合的内容会加到原生CSS中
	```less
	.center {}
	#wrap { .center}
	```
2. 不带输出混合：不会加到原生css中
	```less
	.center() {}
	#wrap { .center}
	```
3. 带参数混合
	```css
	.center(@w,@h) { width:@w; height:@h }
	#wrap { .center(100px,100px) }
	```
4. 带默认值的混合
	```css
	.center(@w:10px,@h:10px) { width:@w; height:@h }
	#wrap { .center(100px,100px) }
```
5. 匹配模式
	```css
	.center(@w,@h) { width:@w; height:@h }
	#wrap { .center(@w:100px,@h:100px) }
```
		也可以使用 `@import './triangle.less';` 引入其他 less 混入（函数）
6. arguments变量
	```css
	.border(@1,@2,@3){
	    border: @arguments;
	}
	
	#wrap > .sjx{
	    .border(1px,solid,black);
	}
	```
	