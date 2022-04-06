<template>
    <!-- 组件的结构 -->
    <div>
        <h2>学生的名称:{{name}}</h2>
        <h2>学生的年龄：{{age}}</h2>
    </div>
</template>

<script>
    // 组件交互下相关的代码
     export default{
         name:'Student',
        data(){
            return {
                name:'张三',
                age:"18"
            }
        },
    }
</script>
