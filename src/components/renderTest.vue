<template>
  <div>
    <p v-if="isShown">Vue is perfect!</p>
    <p v-else>Oh no!😭</p>
<!--  如果想同时切换多个元素的话，可以将它们包裹在template中，最终的渲染结果不包括template元素-->
    <template v-if="isShown">
      <p>你</p>
      <p>好</p>
      <p>啊</p>
    </template>
<!--    和v-if不一样，v-show元素始终会被渲染并被保存在dom中；v-show不支持template分组-->
    <p v-show="!isShown">这个是通过v-show来控制是否展示的</p>
<!--    items是原数组，item是迭代项，index是迭代的索引，v-for必须要有key，可以是迭代项本身，也可以是迭代项的某个属性-->
    <p v-for="(item,index) in items" :key="item">{{item}}-{{index}}</p>
<!--    除了遍历数组以外，也可以遍历对象里面的每个属性-->
<!--    value是值，name是属性名-->
    <p v-for="(value,name) in obj" :key="value">{{name}}:{{value}}</p>
    <button @click="changeContent">更改数组内容</button>
<!--    in后面也可以直接加数字-->
    <span v-for="n in 10" :key="n">{{n}}</span>
  </div>
</template>

<script>
  export default {
    name: "renderTest",
    data(){
      return{
        isShown: false,
        items:[
          1,
          2,
          3
        ],
        obj:{
          name: 'ydl',
          sex: 'male',
          hobby: 'se'
        }
      }
    },
    methods:{
      changeContent(){
        this.items.push(-1)
        this.items.sort()
        this.items.reverse()
        // 只能对数组使用push、pop、shift、sort、reverse方法,这些方法是直接变更了原来的数组
        // this.obj.push({height: '180cm'})
      }
    }
  }
</script>

<style scoped>

</style>