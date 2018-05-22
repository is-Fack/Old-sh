##vue-router
router-link  so（搜索引擎）su（前端优化）
meta:路由元信息
属性
	
	自定义标签：tag
	精准匹配：exact
	绑定事件：event="事件"
路由重定向

	redirect:'域名'
	redirect:(to)=>{
			if(to.path ==='路径'){
				return {path:'要跳转的路径'}
			}else if(to.path ==='路径'){
				return {path:'要跳转的路径'}	
			}
		}
	
	
命名视图
		
	{
		path:
		name:
		compoents:{
			default:组件 (默认路由)
				
		}
	}		
	
路由传参
	
	第一步：在目标路由配置这里path:'/路径/:形参？'
	第二步：在目标router-link配置： :to='/路径/+实参'
	第三部：用路由对象$route获取参数操作；

路由动画

	标签：<transition name='动画css的v'>要执行动画的内容</transition>
	2.设置css
	进入
	v-enter(开始)
	v-enter-active(过度)
	v-enter-to(完毕)
	离开
	v-leave(开始)
	v-leave-active(过度)
	v-leave-to(完毕)


solt

	匿名：
		父：  <children>  
    		  <span>12345</span>//这边不会显示
			 </children>
		子：  template:
				<div><slot></slot>我是子组件</div>	
		结果显示：12345我是子组件
		等于你在父组件里写子组件的内容时，他不知道要加在哪里
		必须写一个slot才能知道写在哪（具体的位置） 
	 
	命名：
		父： <children>
				<span slot='name1'>123456</span>		
		 	 </children>
		子：template:
			<div>
			 <div><slot name='name1'>1</slot></div>	
			 <div><slot name='name2'>2</slot></div>
			</div>
			 
		结果显示：123456
				 2		
		对应名称的slot替换
		适用于使用插槽过多时

		作用域
		（1）、单个页面
		父:<children>
				<template slot='name1' scope='props'>
					<p v-for='val in props.data'>{{val.name}}</p>
				</template>
		   </children>
        子：template:
		  <div>
			<slot name='name1' :data='arr' >123123</slot>
		  </div>	
		,data(){
			return {
				arr:[
						{name:1,id:1},
						{name:2,id:2},
						{name:3,id:3},
						{name:4,id:4},
						]
			}
		}
	
		显示结果：1 2 3 4
		作用域必须用 template标签 scope属性来定义作用域
		（2）、vue-cli
		
		


路由守卫

	概念：在导航前后中进行拦截对导航进行逻辑处理
	分为三种：全局、单个路由、组件

全局：两个(beforeEach(进入路由前)、afterEach(进入路由后))

	router.beforeEach((to, from, next) => {
	  /*
	    to 目标路由
	    from 源路由
	    next 跳转到下一个路由
	  */
	  if (to.meta.login) {
	    // 如果需要，则跳转到登录页
	    next('/login');
	  } else {
	    // 如果不需要，则直接跳转到对应路由
	    next();
	  }
	});

	// 进入路由后方法勾子
	router.afterEach((to, from) => {
	  /*
	    to 目标路由
	    from 源路由
	  */
	  if (to.meta.menuName) {
	    console.log(to.meta.menuName);
	  } else {
	    console.log('暂无名称');
	  }
	});

局部构子函数

	只有一种：beforeEach用法：
	直接写在配置里
	{
	  path: '/angular',
	  name: 'Angular',
	  component: Angular,
	  beforeEnter(to, from, next) {
    /*
      to 目标路由
      from 源路由
      next 跳转到下一个路由
    */
    if (to.meta.menuName) {
      console.log(to.meta.menuName);
    } else {
      console.log('暂无名称');
    }

	
组件路由

	三种：beforeRouteEnter(to,from,next)  进入
		 beforeRouteUpdate(to,from,next) 更新
		  beforeRouteLeave(to,from,next) 离开