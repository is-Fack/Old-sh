##VUEX入门
###零.VUEX的概念
	
	Vuex 是一个专为 Vue.js 应用程序开发的状态管理模式。
	状态可以理解为数据
	它采用集中式存储管理应用的所有组件的状态。
	这里的关键在于集中式存储管理。这意味着本来需要共享状态的更新是需要组件之间通讯的，而现在
	有了vuex，就组件就都和store通讯了。问题就自然解决了
###一.安装vuex

	 cnpm install vuex --save
###二.配置
	
	1.在src里建立一个store文件夹
	2.在store文件夹里建立一个index.js文件
	3.在min.js里引入index.js文件
	import store from '路径'
	4.在el里注册store；
5.在index.s文件写入

	import Vue from 'vue'
	import Vuex from 'vuex'

	Vue.use(Vuex);

export defoult new Vuex.Store({});

###三.入门

1.state://大部分数据、也叫状态

	在组件中通过computed来获取
2.mutations://唯一更改state数据的地方（可传两个参数(state里的数据，传过来的参数)）；

	两种提交方式
	1.this.$store.commit({
		type:'自定义事件'
		,参数:数据
	})
	2.this.$store.commit('自定义事件',{参数:数据})

	在组件中用methods触发this.$store.commit来请求mutation
3.actions（异步请求的时候用actions）
	
	actions修改状态需要一个mutation（重点！！！）
	写法：
	vuex:
	addAction(context){
		context.commit('mutation里的事件',{参数：数据})	
	}	
	vue组件：
	methods里：
	this.$store.dispatah('actions里的事件')；
	
	参数：
	context:类似于store单它是store下的一个对象

4.getters://vuex里的计算属性

	参数：
	stata:state里的数据、状态
	用法与computed一样；

5.models：当页面结构太大，代码过多时用

	定义方法：（与state是同级的）：
	在外边定义一个模板
		let mode={
			state:{状态}
		}
		models:{
			定义的模板
		}
	在组件内取值时通过computed
	return this.$store.state.mode.状态；
	用时不用加模块
	如：this.$store.commit('自定义事件');

###四.什么时候用vuex

	1.多个组件依赖同一状态
	2.组件深层嵌套
	3.来自不同视图的行为需要变更状态；

###五.vuex的逻辑流程

	1.通过component中的某个事件，通过dispatch触发一个action(API接口)
	2.在action中通过commit提交mutation来改变state里的状态
	（改变状态的唯一方式是提交一个mutation）
	3.最后更新到component中