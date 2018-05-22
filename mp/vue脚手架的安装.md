##vue脚手架
是基于webpack2.0搭建的（现在webpack已经有3.0了）
		cnpm install  vue-cli(加个 -g是全局安装) 
 		vue init webpack demo（建立脚手架）
		cnpm install (初始化依赖)
		cnpm run dev 
		cnpm run build(打包生成线上目录)
##包的安装
@（指定版本）

##脚手架的两种模式
hash、history
<router-link tag=""(指定标签)></router-link>

##sass
		cnpm install --save-dev sass-loader
		cnpm install --save-dev node-sass
##vuex
cnpm install vuex --save
##Jquery

	npm install jquery --save-dev 引入jquery。
	在build/webpack.base.conf.js中添加如下内容：
	var webpack = require('webpack')
	和
	plugins: [
	  new webpack.ProvidePlugin({
	    $: "jquery",
	    jQuery: "jquery"
	  })
	],
	
	在src/main.js文件中 引入jquery
	import $ from 'jquery'
###Bootstrap
	命令npm install bootstrap --save-dev
	在src/main.js文件中 引入bootstrap
	import './assets/css/bootstrap.css'
	import './assets/js/bootstrap.min'
	不行就在加一条：
	cnpm install --save poppers.js
###store

		state => 基本数据
		getters => 从基本数据派生的数据 
		mutations => 提交更改数据的方法，同步！ 
		actions => 像一个装饰器，包裹mutations，使之可以异步。 
		modules => 模块化Vuex

###axios
		cnpm install axios
		cnpm install --save axios vue-axios

		import Vue from 'vue'
		import axios from 'axios'
		import VueAxios from 'vue-axios'
		 
		Vue.use(VueAxios, axios)
		
		Vue.axios.get(api).then((response) => {
		  console.log(response.data)
		})
		 
		this.axios.get(api).then((response) => {
		  console.log(response.data)
		})
		 
		this.$http.get(api).then((response) => {
		  console.log(response.data)
		})
###mutations的两种方法

	 第一种提交mutation的方式
      this.$store.commit('方法'{参数})

     第二种提交mutation的方式
      this.$store.commit({
        type: '方法',
        形参: 实参
      })
###amaze UI(妹子UI)
		cnpm install amaze-vue --save
	在vue-cli项目下的package.json文件中，"devDependencies"项中添加    "amaze-vue": "（具体的版本号)"("amaze-vue": "^1.1.12",)
	在项目的根目录下，执行 npm install （将依赖模块的源代码导入到node_modules中）
	在 /src/main.js中添加如下代码
	import AmazeVue from 'amaze-vue';  
	import 'amaze-vue/dist/amaze-vue.css';  

	Vue.use(AmazeVue);  

##element-ui

	cnpm i element-ui@next -D

	main.js配置
	import ElementUI from 'element-ui';
	import 'element-ui/lib/theme-chalk/index.css';

	Vue.use(ElementUI);

##loading动画

	cnpm install vue-loading-template --save

在组件中引入组件
	
	例子：
	<vue-loading type="bars" color="#d9544e" :size="{ width: '50px', height: '50px' }"></vue-loading>
	
	
	import vueLoading from 'vue-loading-template'

	components: {
      vueLoading
    }

	type：(类型:8种)
	balls、bars、beat、bubbles、cylon、spin、spiningDubbles、barsCylon