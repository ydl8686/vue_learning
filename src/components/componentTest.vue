<template>
    <div>
        <li>{{todo.text}}</li>
    </div>
</template>

<script>
    // 父组件传参给子组件步骤
    // 1.子组件中加入props:['XXXX']
    // 2.父组件中:XXXX=xxxx，其中XXXX是子组件中的props，xxxx是父组件中要传递给子组件的数据
    export default {
        name: "componentTest",
        props:[
            'todo'
        ]
    }
</script>

<style scoped>

</style>