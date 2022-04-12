<template>
   <div class="student">
     <h2>姓名:{{  name }}</h2>
     <h2>性别: {{ sex }}</h2>
     <h2>当前求和为:{{number}}</h2>
     <button @click="add">点我number++</button>
     <button @click="sendStudentName">把学生名给App</button>
     <button @click="unbind">解绑atguiug事件</button>
     <button @click="death">销毁当前Student组件的实例(vc)</button>
   </div>
</template>

<script>

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
    add(){
      console.log('add回调被调用了');
      this.number++
    },
    sendStudentName(){
      //emit触发绑定在指定vc上的自定义事件 vc实例对象可以使用该方法
      this.$emit('atguigu',this.name)
      // this.$emit('demo')//同时触发两个事件
    },
    unbind(){
      this.$off('atguigu')//解绑一个自定义事件
      // this.$off(['atguigu','demo'])//解绑多个自定义事件
      // this.$off()//解绑所有的自定义事件
    },
    death(){
      this.$destroy()//销毁当前的Student组件你实例，销毁后所有Student实例的自定义事件全都不奏效
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
