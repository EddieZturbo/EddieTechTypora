# Front-end Dev

## vscode

### JavaScript



## Vue.js

https://vuejs.org/guide/introduction.html

![image-20221217162846197](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221217162846197.png)

### Install vue

https://v2.vuejs.org/v2/guide/installation.html#NPM

使用npm

![image-20221217163501205](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221217163501205.png)

![image-20221217163550739](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221217163550739.png)

![image-20221217172622778](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221217172622778.png)

### mvvm

> 原理：https://segmentfault.com/a/1190000038375749



> 想要Vue工作就必须`创建一个Vue实例`（并且要`传入配置对象`）
>
> **一个Vue实例只能binding一个容器**
>
> 真实`开发中只会有一个Vue实例`并且会配合着`组件`一起使用

![image-20221217170114366](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221217170114366.png)

- MVVM模型：
  - M：模型（Model），data中的数据
  - V：视图（View），模板代码
  - VM：视图模型（ViewModel），Vue实例

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <!--1、导入Vue的包-->
    <script src="https://cdn.jsdelivr.net/npm/vue@2.6.10/dist/vue.js"></script>
</head>
<body>
<!--这个div区域就是MVVM中的 View-->
<div id="div1">
    {{name}}
</div>
</body>

<script>
    // 2、创建一个Vue的实例
    //new出来的对象就是MVVM中的 View Module（调度者）
    var myVue = new Vue({
        el: '#div1', //当前vue对象将接管上面的div1区域(容器和vue实例要一一对应)
        data: {//data就是MVVM中的 module
            name: 'smyhvae'
        }
    });
    myVue.$mount('#div1')//第二种挂载容器的写法{同el: '#div1',}（当前vue对象将接管上面的div1区域(容器和vue实例要一一对应)）
</script>
</html>
```

![image-20230312171603223](C:/Users/ZJH20/AppData/Roaming/Typora/typora-user-images/image-20230312171603223.png)

![image-20230312224053355](C:/Users/ZJH20/AppData/Roaming/Typora/typora-user-images/image-20230312224053355.png)

### Vue Lifecycle

![image-20230327112937791](C:/Users/ZJH20/AppData/Roaming/Typora/typora-user-images/image-20230327112937791.png)

![image-20230327125334668](C:/Users/ZJH20/AppData/Roaming/Typora/typora-user-images/image-20230327125334668.png)

### Vue Component

![image-20230329172014909](C:/Users/ZJH20/AppData/Roaming/Typora/typora-user-images/image-20230329172014909.png)

![image-20230329172155186](C:/Users/ZJH20/AppData/Roaming/Typora/typora-user-images/image-20230329172155186.png)

![image-20230329172214938](C:/Users/ZJH20/AppData/Roaming/Typora/typora-user-images/image-20230329172214938.png)

> 1.一个重要的内置关系：VueComponent.prototype.__proto__ === Vue.prototype
>
> 2.为什么要有这个关系：让组件实例对象（VueComponent）可以访问到 Vue原型上的属性、方法。相当于和vm实例对象一样的功能

![image-20230329191208971](C:/Users/ZJH20/AppData/Roaming/Typora/typora-user-images/image-20230329191208971.png)

### vue instance

![image-20221028220226528](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221028220226528.png)

![image-20221028221803804](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221028221803804.png)

## Vue模块化开发 脚手架工程

```
全局安装webpack

npm install webpack -g
```

![image-20221217223101795](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221217223101795.png)

```
全局安装 vue脚手架

npm install -g @vue/cli-init

npm install --global vue-cli
```

![image-20221217223805568](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221217223805568.png)

### 初始化脚手架vue项目

```
vue init webpack appname

使用vue 通过weback模板初始化一个 名称为appname的项目
```

![image-20221217223849827](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221217223849827.png)

![image-20221217224009846](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221217224009846.png)

![image-20221217224203515](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221217224203515.png)

![image-20221217224245819](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221217224245819.png)

使用VSCode启动

![image-20221217224541631](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221217224541631.png)

![image-20221217224303340](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221217224303340.png)

## Vue-ElementUI

https://element.eleme.cn/#/zh-CN

![image-20221217232802260](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221217232802260.png)

### npm 安装

推荐使用 npm 的方式安装，它能更好地和 [webpack](https://webpack.js.org/) 打包工具配合使用。

```shell
npm i element-ui -S
```

![image-20221217232916534](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221217232916534.png)

![image-20221217232937271](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221217232937271.png)

### 引入 Element

你可以引入整个 Element，或是根据需要仅引入部分组件。我们先介绍如何引入完整的 Element。

#### [¶](https://element.eleme.cn/#/zh-CN/component/quickstart#wan-zheng-yin-ru) 完整引入

在 main.js 中写入以下内容：

```javascript
import Vue from 'vue';
import ElementUI from 'element-ui';
import 'element-ui/lib/theme-chalk/index.css';
import App from './App.vue';

Vue.use(ElementUI);

new Vue({
  el: '#app',
  render: h => h(App)
});
```

以上代码便完成了 Element 的引入。需要注意的是，样式文件需要单独引入。

![image-20221217233124406](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221217233124406.png)

### Vue模板

```html
{
	"生成vue模板": {
		"prefix": "vue",
		"body": [
			"<template>",
			"<div></div>",
			"</template>",
			"",
			"<script>",
			"//这里可以导入其他文件（比如：组件，工具js，第三方插件js，json文件，图片文件等等）",
			"//例如：import 《组件名称》 from '《组件路径》'",
			"",
			"export default {",
			"//import引入的组件需要注入到对象中才能使用",
			"components: {},",
			"props: {},",
			"data() {",
			"//这里存放数据",
			"return {};",
			"},",
			"//计算属性 类似于data概念",
			"computed: {},",
			"//监控data中的数据变化",
			"watch: {},",
			"//方法集合",
			"methods: {},",
			"//声明周期 - 创建完成（可以访问当前this实例）",
			"created() {},",
			"//声明周期 - 挂载完成（可以访问DOM元素）",
			"mounted() {},",
			"beforeCreate() {}, //生命周期 - 创建之前",
			"beforeMount() {}, //生命周期 - 挂载之前",
			"beforeUpdate() {}, //生命周期 - 更新之前",
			"updated() {}, //生命周期 - 更新之后",
			"beforeDestroy() {}, //生命周期 - 销毁之前",
			"destroyed() {}, //生命周期 - 销毁完成",
			"activated() {} //如果页面有keep-alive缓存功能，这个函数会触发",
			"};",
			"</script>",
			"<style scoped>",
			"</style>",
		]
	}
}
```

