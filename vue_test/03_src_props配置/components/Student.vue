<template>
  <div>
    <h1>{{ msg }}</h1>
    <h2>学生的名称:{{ name }}</h2>
    <h2>学生的性别:{{ sex }}</h2>
    <h2>学生的年龄:{{myAge+1}}</h2>
    <button @click="updataAge">尝试修改收到的年龄</button>
  </div>
</template>

<script>
export default {
  name: "Student",
  data() {
    return {
      msg: "我是学习Vue的菜鸟",
      myAge:this.age
    };
  },
  methods: {
    updataAge() {
      this.myAge=this.myAge+1
    },
  },
  props:['name','sex','age'] //简单接受
  // 接收的同时进行类型限制
  /*  props:{
        name:String,
        sex:String,
        age:Number
    } */
  //接收的同时进行类型限制:默认值的指定，必要性限制
  /* props: {
    name: {
      type: String, //name的类型是字符串
      requird: true, //name是必要的
    },
    age: {
      type: Number,
      default: 99, //默认值
    },
    sex: {
      type: String,
      requird: true, //name是必要的
    },
  }, */
};
</script>

<style>
</style>