#vue
>  Vue是一个前端的双向数据绑定类的框架
>  构建用户界面的渐进式JavaScript 框架
# 引入vue的两种方式
* 直接引入vue.js            
    *  ```<script src="https://cdn.jsdelivr.net/npm/vue"></script>```
    *  ```<script src="vue.js"></script>```
* 命令行工具 (CLI)
     ### 全局安装 vue-cli
      $ npm install --global vue-cli
     ### 创建一个基于 webpack 模板的新项目
      $ vue init webpack my-project
     ### 安装依赖
      $ cd my-project
      $ npm install
      $ npm run dev

* computed属性 和 watcher  
    ## computed属性
    * 对于所有复杂逻辑，你都应该使用 computed 属性(computed property)
    * computed 属性会基于它所依赖的数据进行缓存
    * Vue 其实还提供了一种更加通用的方式，来观察和响应 Vue 实例上的数据变化：watch 属性
    * 相比watch,更好的使用 computed 
    * computed 属性中设置 setter
    ## watcher
      
