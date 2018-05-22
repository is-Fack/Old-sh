##MVC与MVVM

	mvc:model controller view
	mvvm:model view viewmodel
##双向数据绑定
	渐进式框架：需要什么，就加载 什么，优化性能
##v-if与v-show

	1.v-show通过css样式来显示隐藏
	v-if是来动态创建删除节点
	2.使用场景
	v-show:操作频繁
	v-if:偶尔需显示隐藏
	3.作用域
	v-if会形成一个新的作用域	
##computed和watch的区别
	computed：写法更加简洁、会缓存数据、性能更好
	watch : 
##过滤器
内置过滤器

	作用：按既定的规则对数据的格式化；
	使用方式：{{数据.}} 
自定义过滤器

	分为两种：局部定义，全局定义
	局部：new Vue({
			filters:{
				'过滤器名称':callback
			}
	})
	全局: vue.filter('自定义名称'，function(val){})
		
##自定义指令
全局directive

	Vue.directive('自定义事件名',{
			生命周期:function(元素){
				操作
			}
		})
局部directive

	new Vue({
		directive:{
			事件名：{
			生命周期: function (el) {
		        // 聚焦元素
		        el.focus()
			}
		}	
	})

$event

##本地存储
	localStorage:永久存储 ，手动删除，数据共享
	sessionStorage：临时存储，关闭浏览器（结束进程）便会消失页面与页面间是独立的

方法

	setItem(key,val)设置数据
	getItem()获取数据
	removeItem()删除指定数据
	clear()清空

##组件
组件通信
	父传子：
		父组件通过绑定自定义属性来传递
		子组件通过props来接收自定义事件
	
	子传父：
		子组件通过this.$emit('自定义事件',要传的数据)；
		父组件通过methods定义一个方法来接收


	兄弟通信
	第一种：子-》父（中转）-》子（层层传递，很繁琐容易传晕）
	第二种：建立一个空的vue实例进行中转

内置组件
	<keep-alive>
	<component :is='data里的值'></component>	
	</keep-alive>