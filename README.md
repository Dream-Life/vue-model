# vue-model
在vue中使用面向对象class开发，使class的公有数据双向绑定；

如果不需要使用双向绑定可以将属性通过Symbol私有化

## 安装

```shell
npm install 
or 
yarn add 
```

## 配置

```javascript
// model/hello.js
class Hello{
  // constructor如果有参数传入需要配置默认值
  // 目前需要自己创建init方法初始化数据
  constructor(){
    // msg双向绑定，数据修改后组件会更新
    // 目前对对象，数组可能存在bug，正在后续开发
    this.msg = 'Hello'
  }
  // 初始化方法名不一定是init，你可以自己命名
  init(m){
    this.msg = m
  }
  setMsg(v){
    this.msg = v
  }
}
```



```javascript
// main.js
import Vue from 'vue'
import Models from ''
import Hello from './model/hello.js'
Vue.use(Models)

const model = new Models({
  hello: Hello
})

// 配置好后可以在所有组件中使用，
// 使用class变量this.$model.hello.msg
// 使用class方法this.$model.hello.setMsg('Bye')
new Vue({
  el:'#app',
  model
})
```

