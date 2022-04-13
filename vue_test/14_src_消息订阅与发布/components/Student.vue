<template>
   <div class="student">
     <h2>姓名:{{  name }}</h2>
     <h2>性别: {{ sex }}</h2>
     <button @click="sendStudentName">把学生名传递给school组件</button>
   </div>
</template>

<script>
import pubsub from 'pubsub-js'
export default {
  name: "Student",
  data(){
    console.log(this);
    return {
       name: '张三',
       sex: '男',
       number:0
    }
  },
  methods: {
    sendStudentName(){
      pubsub.publish('hello',666)
    }
  },

}
</script>

<style scoped>
  .student{
    background: orange;
    padding: 5px;
    margin-top: 30px;
  }
</style>
