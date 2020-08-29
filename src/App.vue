<template>
  <div id="app">
    <ol>
<!--      使用test和Test都行-->
      <Test v-for="item in thing" :todo="item" :key="item.text"></Test>
    </ol>
    <Test :todo="thing[0]"></Test>
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
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

export default {
  name: 'app',
  components: {
    HelloWorld,
    Test
  },
  data(){
    return{
      thing: [
        { text: '我是靓仔'},
        { text: '我是靓女'},
      ]
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
</style>
