#结构伪类选择器
	1.作用与优势：
		1. 作用：根据元素在HTML中的结构关系查找元素
		2.优势：减少对于HTML中类的依赖，有利于保持代码整洁
		3.场景：常用于查找某父级选择器中的子元素
	2.选择器
		选择器                说明
		E:first-child    匹配父元素中第一个子元素，并且是E元素
		E:last-child     匹配父元素中最后一个子元素，并且是E元素
		E:nth-child(n)      匹配父元素中第n个子元素，并且是E元素
		E:nth-last-child(n) 匹配父元素中倒数第n个子元素，并且是E元素
	3.n的注意点：
		1.n为：0、1、2、3、4、5、6、….
		2.通过n可以组成常见公式
				功能               公式
				偶数              2n、even
				奇数              2n+1、2n-1、odd
				找到前5个              -n+5
				找到从第5个往后         n+5

	4.(拓展补充)nth-of-type
		1.选择器：
			E:nth-of-type(n)     只在父元素的同类型(E)子元素范围中，匹配第n个
		2.区别：
			:nth-child→直接在所有孩子中数个数
			：nth-of-type一先通过该 类型 找到符合的一堆子元素，然后在这一堆子元素中数个数
#伪元素
	1.伪元素：一般页面中的非主体内容可以使用伪元素
	2.区别：
		1. 元素：HTML设置的标签
		2. 伪元素：由CSS模拟出的标签效果
	3.种类：
		伪元素                   作用
		：：before       在父元素内容的最前添加一个伪元素
		：：after        在父元素内容的最后添加一个伪元素
	4.注意点：
		1.必须设置content属性才能生效
		2.伪元素默认是行内元素
#标准流
	1.标准流：又称文档流，是浏览器在渲染显示网页内容时默认采用的一套排版规则，规定了应该以何种方式排	列元素
	2.常见标准流排版规则：
		1.块级元素：
				 从上往下，垂直布局，独占一行
		2.行内元素 或 行内块元素：
			 从左往右，水平布局，空间不够自动折行
#浮动
	1.浮动的作用：
		1.早期：图文环绕
		2.现在：
			让垂直布局的盒子变成水平布局，如：一个在左，一个在右
	2.代码：
		1.属性名：float
		2.取值：
			1.left     左浮动
			2.right    右浮动
	3.浮动特点：
		1.浮动元素会脱离标准流(简称：脱标)，在标准流中不占位置
			. 相当于从地面飘到了空中
		2.浮动元素比标准流高半个级别，可以覆盖标准流中的元素
		3.浮动找浮动，下一个浮动元素会在上一个浮动元素后面左右浮动
		4.浮动元素会受到上面元素边界的影响
		5.浮动元素有特殊的显示效果
			.一行可以显示多个
			.可以设置宽高
	4.注意点：
		浮动的元素不能通过text-align:center或者margin:0 auto，让浮动元素本身水平居中



#清除浮动：
	1.清除浮动的介绍
		1. 含义：
				清除浮动带来的影响
		2. 影响：
				如果子元素浮动了，此时子元素不能撑开标准流的块级父元素
		3. 原因：
				子元素浮动后脱标→不占位置
		4. 目的：
				需要父元素有高度，从而不影响其他网页元素的布局
	2.清除浮动的方法：
		1.直接设置父元素的高度
			1.优点：简单粗暴，方便
			2.缺点：有些布局不能固定父元素的高度  如：京东推荐模块。新闻列表
		2.额外标签法；
			1.操作：
				1. 在父元素内容的最后添加一个块级元素
				2. 给添加的块级元素设置clear:both
			2.特点：
			3.缺点：会在页面中添加额外的标签，会让页面的HTML结构变得复杂
    3.单伪元素清除法：
		1.操作：用伪元素替代了额外标签
		①：基本写法            			②：补充写法
		.clearfix::after {
		    content:''; 				.clearfix::after {
			display:block;					content:'';
			clear:both;						display:block;
		}    	    						clear:both;
											/* 补充代码：在网页中看不到伪元素*/
		     								height:0;
		         							visibility:hidden;
										}
		
		2.优点：项目中使用，直接给标签加类即可清除浮动
	4.双伪元素清除法：
		1.操作：
			.clearfix::before,
			.clearfix::after〔
				content:'';
				display:table;
			}
			.clearfix::after{
			clear:both;
			}
		2.优点：项目中使用，直接给标签加类即可清除浮动

	5.给父元素设置overflow:hidden
		1.直接给父元素设置overflow:hidden
		2.优点：方便
#BFC的介绍
	1.块格式化上下文(Block Formatting Context):BFC
		.是Web页面的可视CSS渲染的一部分，是块盒子的布局过程发生的区域，也是浮动元素与其他元素交互的区域。
	2.创建BFC方法：
		1.html标签是BFC盒子
		2.浮动元素是BFC盒子
		3.行内块元素是BFC盒子
		4.overflow属性取值不为visible。如：auto、hidden...
		5.......
	3.BFC盒子常见特点：
		1.BFC盒子会默认包裹住内部子元素(标准流、浮动)→应用：清除浮动
		2.BFC盒子本身与子元素之间不存在margin的塌陷现象→应用：解决margin的塌陷
		3.….…
#定位
##常见布局方法
	1. 标准流
		1.块级元素独占一行→垂直布局
		2.行内元素/行内块元素一行显示多个 → 水平布局
	2. 浮动
		1.可以让原本垂直布局的 块级元素变成水平布局
	3. 定位
		1. 可以让元素自由的摆放在网页的任意位置
		2.一般用于 盒子之间的层叠情况
	4.定位的使用场景：
		1.解决盒子与盒子之间的层叠问题
		2.让盒子始终的固定在屏幕中的某个位置
##静态定位
	1.介绍：静态定位是默认值，就是之前认识的标准流。
	2.代码：
			position:static;
			方位词：偏移值；
			方位词：偏移值；        //方位词水平和垂直各选一个
	3.注意点：
		1.静态定位就是之前标准流，不能通过方位属性进行移动
		2.之后所说的定位不包括静态定位，一般特指后面几种：相对，绝对，固定
##相对定位
	1.介绍：自恋型定位，相对于自己之前的位置进行移动
	2.代码：
			position:relative;
			方位词：偏移值；
			方位词：偏移值；        //方位词水平和垂直各选一个
	3.特点：
		1.需要配合方位属性实现移动
		2.相对于自己原来位置进行移动
		3.在页面中占位置→没有脱标
	4.应用场景：
		1.配合绝对定位组CP(子绝父相)
		2.用于小范围的移动
##绝对定位
	1.介绍：拼爹型定位，相对于非静态定位的父元素进行定位移动
	2.代码：
			position:absoulte;
			方位词：偏移值；
			方位词：偏移值；        //方位词水平和垂直各选一个
	3.特点：
		1.需要配合方位属性实现移动
		2.默认相对于浏览器可视区域进行移动
		3.在页面中不占位置→已经脱标
	4.应用场景：
		1.配合绝对定位组CP(子绝父相)
	5.绝对定位相对于谁移动？
		1.祖先元素中没有定位一默认相对于浏览器进行移动
		2.祖先元素中有定位一相对于 最近的 有定位 的祖先元素进行移动

##子绝父相
	1.场景：让子元素相对于父元素进行自由移动
	2.含义：
		子元素：绝对定位
		父元素：相对定位
	3.子绝父相好处：
		父元素是相对定位，则对网页布局影响最小
	4.(拓展补充)子绝父绝特殊场景
		1.场景：
			在使用子绝父相的时候，发现父元素已经有绝对定位了，此时直接子绝即可！
		2.原因：
			父元素已经有定位已经满足要求，如果盲目修改父元素定位方式，可能会影响之前写好的布局
##固定定位
	1.介绍：死心眼型定位，相对于浏览器进行定位移动
	2.代码：
			position:fixed;
			方位词：偏移值；
			方位词：偏移值；        //方位词水平和垂直各选一个
	3.特点：
		1.需要配合方位属性实现移动
		2.相对于浏览器可视区域进行移动
		3.在页面中不占位置→已经脱标
	4.应用场景：
		1.让盒子固定在屏幕中的某个位置
##元素层级关系
	1.不同布局方式元素的层级关系：
		标准流<浮动<定位
	2.不同定位之间的层级关系：
		1.相对、绝对、固定默认层级相同
		2.此时HTML中写在下面的元素层级更高，会覆盖上面的元素
	3.更改定位元素的层级
		1.场景：改变定位元素的层级
		2.属性名：z-index
		3.属性值：数字
			数字越大，层级越高
#装饰
##垂直对齐方式
	1.基线：浏览器文字类型在元素排版中存在用于对齐的基线（baseline）
	2.场景：解决行内和行内块元素垂直对齐问题
	3.属性名：
		vertical-align
	4.属性值：
		baseline     默认，基线对齐
		top          顶部对齐
		middle       中部对齐
		bottom       底部对齐
##(拓展补充)项目中 vertical-align可以解决的问题
	1.文本框和表单按钮无法对齐问题
	2.input和img无法对齐问题
	3.div中的文本框，文本框无法贴顶问题
	4.div不设高度由img标签撑开，此时img标签下面会存在额外间隙问题
	5.使用line-height让img标签垂直居中问题
##光标类型
	1.场景：设置鼠标光标在元素上时显示的样式
	2.属性名：
		cursor
	3.常见属性值：
		default 默认值，通常是箭头
		pointer 小手效果，提示用户可以点击
		text 工字型，提示用户可以选择文字
		move 十字光标，提示用户可以移动
##边框圆角
	1.场景：让盒子四个角变得圆润，增加页面细节，提升用户体验
	2.属性名：
		border-radius
	3.常见取值：
		数字+px、百分比
	4.赋值规则：
		从左上角开始赋值，然后顺时针赋值，没有赋值的看对角！
	5.画正圆：
		1.盒子是正方形
		2.设置->border-radius：50%
	6.画胶囊
		1.盒子必须是长方形
		2.设置->border-radius：盒子高度的一半
##overflow溢出部分显示效果
	1.溢出部分：指的是盒子 内容部分 所超出盒子范围的区域
	2.场景：控制内容溢出部分的显示效果，如：显示、隐藏、滚动条.....
	3.属性名：
		overflow
	4.常见属性值：
		visible 默认值，溢出部分可见
		hidden 溢出部分隐藏
		scroll 无论是否溢出，都显示滚动条
		auto 根据是否溢出，自动显示或隐藏滚动条
##元素隐藏本身
	1.场景：让某元素本身在屏幕中不可见。如：鼠标：hover之后元素隐藏常见属性：
		1.visibility:hidden
		2.display:none
	2.区别：
		1.visibility:hidden 隐藏元素本身，并且在网页中 占位置
		2.display:none 隐藏元素本身，并且在网页中 不占位置
	3.注意点：
		1.开发中经常会通过 display属性完成元素的显示隐藏切换
		2.display：none；(隐藏)、display：block；(显示)
##(拓展补充)元素整体透明度
	1.场景：让某元素整体(包括内容)一起变透明
	2.属性名：
			opacity
	3.属性值：0~1之间的数字
		·1：表示完全不透明
		.0：表示完全透明
	4.注意点：
		opacity会让元素整体透明，包括里面的内容，如：文字、子元素等....
##(拓展补充)边框合并
	1.场景：让相邻表格边框进行合并，得到细线边框效果
	2.代码：
		border-collapse:collapse;
#选择器拓展
##链接伪类选择器
	1.场景：常用于选中超链接的不同状态
	2.选择器语法：
		a:link f) 选中a链接 未访问过的状态
		a:visited f) 选中a链接 访问之后 的状态
		a:hover f 选中鼠标悬停的状态
		a:active ( 选中鼠标按下的状态
	3.注意点：
		.如果需要同时实现以上四种伪类状态效果，需要按照 LVHA顺序书写
		.记忆口诀：男盆友送了你一个LV包包，你开心的HA哈笑
		.其中：hover伪类选择器使用更为频繁，常用于选择各类元素的悬停状态
##焦点伪类选择器
	1.场景：用于选中元素获取焦点时状态，常用于表单控件
	2.选择器语法：
		input:focus {
		background-color:skyblue;
		}
	3.效果：
		. 表单控件获取焦点时默认会显示外部轮廓线
##属性选择器
	1.场景：通过元素上的HTML属性来选择元素，常用于选择input标签
	2.选择器语法：
		1.E[attr] 选择具有attr属性的E元素
		2.E[attr="val"] 选择具有attr 属性并且属性值等于val的E元素
#CSS样式补充
##精灵图
	1.场景：项目中将多张小图片，合并成一张大图片，这张大图片称之为精灵图
	2.优点：减少服务器发送的次数，减轻服务器的压力，提高页面的加载速度
	3.使用步骤：
		1.创建一个盒子
		2.通过pxcode了量取小图片的大小，将小图片的宽高设置给盒子
		3.将精灵图设置为盒子的背景图片
		4.通过pxcode测量小图片左上角坐标，分别去负值设置给盒子的background-position：x y
##背景图片的大小
	1.作用：设置背景图片的大小，
	2.语法：
		background-size：宽度 高度；
	3.取值：
		1.数字+px             简单方便，常用
		2.百分比           相对于当前盒子自身的宽高百分比
		3.contain         包含，将背景图片等比例缩放，直到不会超出盒子的最大
		4.cover           覆盖，将背景图片等比例缩放，直到刚好填满整个盒子没有空白
##阴影
	1.文字阴影
		1.作用：给文字添加阴影效果，吸引用户注意属性名：text-shadow
		2.取值：
			h-shadow    必须，水平偏移量。允许负值
			v-shadow    必须，垂直偏移量。允许负值
			blur           可选，模糊度
			color          可选，阴影颜色
		3.拓展：
			.阴影可以叠加设置，每组阴取值之间以逗号隔开
	2.盒子阴影
		1.作用：给盒子添加阴影效果，吸引用户注意，体现页面的制作细节属性名：box-shadow
		2.取值：
				h-shadow        必须，水平偏移量。允许负值
				v-shadow        必须，垂直偏移量。允许负值
				blur               可选，模糊度
				spread             可选，阴影扩大
				color              可选，阴影颜色
				inset              可选，将阴影改为内部阴影
##过渡
	1.作用：让元素的样式慢慢的变化，常配合hover使用，增强网页交互体验属性名：transition
	2.常见取值：
		过渡的属性  （a11）：所有能过渡的属性都过渡、（具体属性名）如：width：只有width有过渡
		过渡的时长   数字+s（秒)
	3.注意点：
		1.过渡需要：默认状态和hover状态样式不同，才能有过渡效果
		2.transition属性给需要过渡的元素本身加
		3.transition属性设置在不同状态中，效果不同的
			1. 给默认状态设置，鼠标移入移出都有过渡效果
			2. 给hover状态设置，鼠标移入有过渡效果，移出没有过渡效果
##SEO三大标签
	1.title ：网页标题标签
	2.description  网页描述标签
	3.keywords     网页关键词标签
##(拓展补充)有语义的布局标签
	1.场景：在HTML5新版本中，推出了一些有语义的布局标签，可以增强网页的语义化标签：
		header 网页头部
		nav 网页导航 
		footer 网页底部
		aside 网页侧边栏
		section 网页区块
		article 网页文章
	2.注意点： 
		.以上标签显示特点和div一致，但是比div多了不同的语义
##版心
	1.场景：把页面的主体内容约束在网页中间
	2.作用：让不同大小的屏幕都能看到页面的主体内容
	3.代码：
			/* 版心 */
			.container{
				width:1240px;
				margin:0 auto;
			}
	4.注意点：
		.版心类名常用：container、wrapper、w等
##CSS书写顺序
	顺序 类别 属性
	1.布局属性          display、position、float、clear、visibility、overflow
	2.盒子模型+背景     width、 height、 margin、padding、 border.ackground
	3.文本内容属性      color、font、text-decoration、text-align、line-height
	4.点缀属性          cursor、border-radius、text-shadow、box-shadow
#平面转换(空间转换一样的写法，只不过多了一个Z轴）
	1.介绍：改变盒子在平面内的形态（位移，旋转，缩放）
	2.代码：transform
	3.注意点：
		1.在使用空间转换时最好使用perspective属性实现透视的效果，因为要观察到Z轴的变化（不使用的话，人的肉眼观察不到Z轴的变化）  
			.该属性加在父元素上
		2.Z轴的实现效果就是近小远大，也就是我们看到的元素变大了，那是因为元素离我们近了，所以我们看到的相同大小的元素，我们所看到的更大了。
		3.perspective就相当于我们的眼睛里屏幕的远近（最后的取值是200--1200）
##位移
	1.transform：translate（水平移动距离， 垂直移动距离）  （transform：translate3d（x，y，z）
	2.取值（正负均可）
		1.像素单位参照值
		2.百分比（参照物为盒子自身的尺寸）
	3.技巧
		1.translate只给出一个值，表示x轴的移动距离
		2.单独设置某个方向的移动距离：translateX() & translateY()；

##旋转
	1.transform：rotate（角度）
		.角度的单位是deg
	2.取值取正负均可
	3.注意：
		.在旋转时最好设置一下过渡时长

	4.转换原点：
		.使用transform-origin属性改变转换的原点
	5.语法：
		1.默认转换原点是盒子的中心点
		2.transform-origin：原点水平位置 原点垂直位置    中间以空格隔开
	6.取值：
		1.方位名词（top，left ，center......）
		2.像素单位数值
		3.百分比（参照自身的盒子的尺寸计算）
	**7.注意点**
		1.在复合转换时：边旋转变位移
		2.transform：translate（） rotate（）；中间以空格隔开
		3.当 旋转在前 移动在后，效果就是一个大风车吱呦呦滴转

##缩放
	1.语法：transform：scale（x轴缩放倍数，y轴缩放倍数）
	2.技巧：
		.一般下，只设置一个值，表示x轴和y轴等比例缩放
			transform：scale（缩放倍数）
##渐变
	1.渐变是多个颜色逐渐变化的视觉效果，一般用于设置盒子的背景
	2.语法：
		1.background-image：linear-gradient（red ， bule）
			现在基本不用这种
		2.background-image：linear-gradient（
			transparent，
			rgba（0,0,0，.6）
		  ）
			现在用的多，例如华为的卡片
##空间转换的立体呈现
	1.语法：
		.父元素添加transform-style：preserve-3d；   使子元素处于真正的3d空间
	2.步骤：
		1.盒子父元素设置transform-style：preserve-3d；
		2.按需求设置子盒子的位置（位移或者旋转）




	
