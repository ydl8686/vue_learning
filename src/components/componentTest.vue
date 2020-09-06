<template>
    <div>
<!--        子组件上的class和父组件使用子组件的class会并存，不会覆盖-->
        <li>{{todo.text}}</li>
    </div>
</template>

<script>
    // 父组件传参给子组件步骤
    // 1.子组件中加入props:['XXXX']
    // 2.父组件中:XXXX=xxxx，其中XXXX是子组件中的props，xxxx是父组件中要传递给子组件的数据
    // 3.props是和name、data同级别的，不是在return里面！！！
    export default {
        name: "componentTest",
        props:[
            'todo'
        ]
    }
</script>

<style scoped>

</style>