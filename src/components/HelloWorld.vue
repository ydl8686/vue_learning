<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <span :title="message">
    title属性可以指示鼠标停放时的文本
    </span>
    <p v-if="seen">v-if来控制是否显示</p>
    <ol>
<!--      这里的for循环渲染，绑定在哪个组件，就相当于把这个组件copy多少份，并且必须要指定:key-->
      <li v-for="todo in things" :key="todo.text">
        {{ todo.text }}
      </li>
    </ol>
    <button @click="addElement">@click绑定点击事件</button>
<!--    v-model可以实现双向绑定，用户输入的内容绑定到messages-->
    <input v-model="messages">
    <p>{{messages}}</p>
  </div>
</template>

<script>
export default {
  //组件的名字
  name: 'HelloWorld',
  //data是一个函数，本页面需要的数据在return里面返回
  data(){
    return{
      msg: 'hello,nju!',
      // 在文本中添加函数
      message: '8023'+new Date().toLocaleString(),
      // 只有字符串类型的需要加引号
      seen: true,
      things:[
        { text: '学习 JavaScript' },
        { text: '学习 Vue' },
        { text: '整个牛项目' }
      ],
      messages: '蛤'
    }
  },
  //methods本身不是一个方法，所以直接:和花括号
  methods:{
    //普通函数一般都是需要圆括号来接受参数的
    addElement(){
      //从methods里的方法来访问data里返回的数据需要使用this
      this.things.push({text: '新元素'})
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
