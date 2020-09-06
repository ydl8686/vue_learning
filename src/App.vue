<template>
  <div id="app">
    <ol>
<!--      使用test和Test都行-->
<!--      这里的todo是子组件的prop-->
      <Test v-for="item in thing" :todo="item" :key="item.text"></Test>
    </ol>
      <Prop :prop1="p"></Prop>
    <Test :todo="thing[0]"></Test>
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld :prop2="isDisabled" msg="Welcome to Your Vue.js App"/>
    <h4 v-bind:id="'list'+dynamicId">这个h4的id可以随意更改，而采用不同的样式;给属性加上v-bind，就可以变成动态的了，下面button同理</h4>
<!--    绑定id、class还有更高级的办法-->
<!--    这里不同的class可以并存，相当于class="sta active"-->
<!--    <p class="sta" v-bind:class="{active: isActive}">动态切换class,active这个class是否存在取决于isActive的布尔值</p>-->
    <p class="sta" v-bind:class="classObj">这个是class绑定到一个对象上</p>
<!--    除了对象的方式以外，还有数组,下面这么写，三元表达式确定是否采用active这个class，但是errorClass是肯定添加进去的-->
<!--    <p v-bind:class="[isActive? 'active' :'',errorClass]">hhhhhh</p>-->
    <button v-bind:disabled="isDisabled">disable是否动态,绑定的值可以使用完全的js表达式操作，看上面的字符串相加操作例子</button>
    <button @submit.prevent="onsubmit">句点运算符指出触发的事件应该以特殊的方式绑定，阻止组件默认事件发生</button>
    <computed></computed>
    <render></render>
  </div>
</template>

<script>
// 组件封装使用步骤：
// 1.完成组件页面xxx.vue
// 2.import XXX from 'xxxx'，注意这里的XXX和xxxx里的名字可以不一样，使用组件的页面只需要知道XXX
// 3.在div中以标签的形式来使用
// 4.组件的封装不涉及路由
import HelloWorld from './components/HelloWorld.vue'
import Test from './components/componentTest'
import Prop from './components/componentTestAgain'
import Computed from './components/computedTest'
import Render from './components/renderTest'
export default {
  name: 'app',
  components: {
    HelloWorld,
    Test,
    Prop,
    Computed,
    Render
  },
  data(){
    return{
      thing: [
        { text: '我是靓仔'},
        { text: '我是靓女'},
      ],
      p: '这是父组件传过来的属性',
      dynamicId: 'HRed',
      isDisabled: true,
      isActive: true,
      error: null
    }
  },
  // 先created函数，后mounted函数
  // 本身就是函数，不需要：{}
  created() {
      // eslint-disable-next-line no-console
    console.log('8023')
  },
  mounted() {
      // eslint-disable-next-line no-console
      console.log('qzx')
  },
  computed:{
    classObj(){
      return{
        active: this.isActive && !this.error
      }
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
#listHBlue{
  color: blue;
}
#listHRed{
  color: red;
}
.active{
  color: green;
}
.sta{
  font-size: 32px;
}
</style>
