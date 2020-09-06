<template>
<!--    不仅可以像App里面绑定class、id，还可以绑定style；下面这个👇是对象数组-->
    <div v-bind:style="[styleObj,baseStyle]">
        {{prop1}}
    </div>
</template>

<script>
    export default {
        name: "componentTestAgain",
        props:[
            'prop1'
        ],
        data(){
            return{
                styleObj:{
                    color: 'red',
                    fontSize: '23px'
                },
                baseStyle:{
                    margin: '40px'
                }
            }
        }
    }
</script>

<style scoped>

</style>