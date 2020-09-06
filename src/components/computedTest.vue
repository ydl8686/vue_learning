<template>
  <div>
    <p>原来的msg:{{msg}}</p>
    <p>此处插值使用了computed计算:{{reversedMsg}}</p>
    <button @click="changeMsg">改变msg</button>
  </div>
</template>

<script>
  export default {
    name: "computedTest",
    data(){
      return{
        msg:'hello'
      }
    },
    //记住computed的写法，和data不一样，computed是函数的集合，函数名就是要计算的数据名，而data本身就是一个函数，把要返回的数据全部在return里返回
    //也可以在methods里面定义一个reversedMsg方法，然后在插值表达式中直接调用这个函数；但是需要注意的是：
    //computed采用了缓存机制，而methods每次都会重新计算
    computed:{
      reversedMsg(){
        //在这里是可以访问到data中返回的数据的，但是得this.
        return this.msg.split('').reverse().join('')
      }
    },
    methods:{
      changeMsg(){
        this.msg=this.msg+'8023'
      }
    },
    //watch里面的函数名就是数据，如果发生了变化就会自动执行对应的代码
    watch:{
      msg(){
        // eslint-disable-next-line no-console
        console.log('msg发生了变化')
      }
    }
  }
</script>

<style scoped>

</style>