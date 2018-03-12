## object.freeze()  这会阻止修改现有的属性，也意味着响应系统无法再追踪变化。
```
var obj = {
        foo:'bar'
    }
    Object.freeze(obj)

```
## 它们都有前缀 $，以便与用户定义的属性区分开来。
```
 var vm = new Vue({
        el:'#app',
        data:data
    })
    vm.$data === data
    vm.$el === document.getElementById('app')
```

## 生命周期钩子
## 模板语法
* {{}}
* v-html
* v-bind {{}}语法不能作用在 HTML 特性上，遇到这种情况应该使用 v-bind 指令：
* 使用 JavaScript 表达式  eg: {{ number + 1 }}
* 指令
    >> 指令 (Directives) 是带有 v- 前缀的特殊属性,当表达式的值改变时，将其产生的连带影响，响应式地作用于 DOM
    * v-if 
* 参数 一些指令能够接收一个“参数”
    >>
    ```
       <a v-bind:href="url">...</a>
       <a v-on:click="doSomething">...</a>
    ```
* 修饰符
    >> 以半角句号 . 指明的特殊后缀,用于指出一个指令应该以特殊方式绑定
    * .prevent 修饰符告诉 v-on 指令对于触发的事件调用 event.preventDefault()：
    ```
        <form v-on:submit.prevent="onSubmit">...</form>
    ```
* 缩写
    * v-bind >> :   (<a v-bind:href="url"></a>  >>  <a :href="url"></a> )
    * v-on >> @     (<a v-on:click="doSomething"</a> >> <a @:click="doSomething"</a> )
    
## 计算属性和侦听器(computed)
* 计算属性的 getter setter
```
        var vm = new Vue({
            el:'#app',
            data:{
                firstName:'Foo',
                lastName:'Bar'
            },
            computed:{
                fullName:{
                    get:function(){
                        return this.firstName + '' +this.lastName
                    },
                    set:function(newValue){
                        var names = newValue.split(' ')
                        this.firstName = names[0]
                        this.lastName = names[names.length - 1]
                        console.log(newValue)
                        console.log(names)
                    }
                }
            }
        })
        vm.fullName = 'John Doe'
```
* 侦听器 watch
## Class 与 Style 绑定
* 对象语法
```
    <span v-bind:class="{active: isActive}"></span>
    <span v-bind:class="classObject"></span>
```
# 条件渲染
* v-if v-else-if v-else
* 用 key 管理可复用的元素
* v-show
>> v-if vs v-show
    * v-if 是“真正的”条件渲染，因为它会确保在切换过程中条件块内的事件监听器和子组件适当地被销毁和重建。v-if 也是惰性的：如果在初始渲染时条件为假，则什么也不做——直到条件第一次变为真时，才会开始渲染条件块。相比之下， v-show 就简单得多——不管初始条件是什么，元素总是会被渲染，并且只是简单地基于 CSS 进行切换。一般来说， v-if 有更高的切换开销，而 v-show 有更高的初始渲染开销。因此，如果需要非常频繁地切换，则使用 v-show 较好；如果在运行时条件不太可能改变，则使用 v-if 较好。
* 当 v-if 与 v-for 一起使用时，v-for 具有比 v-if 更高的优先级。