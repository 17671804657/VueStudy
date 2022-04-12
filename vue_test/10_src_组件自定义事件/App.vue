<template>
  <div class="app">
    <h1>{{ msg }},学生的姓名是：{{ studentName }}</h1>
    <!--通过父组件给子组件传递函数类型的props实现:子给父传递数据  -->
    <School :getSchoolName="getSchoolName" />
    <hr />
    <!-- 通过父组件给子组件绑定一个自定义事件实现:子给父传递数据(第二种写法,使用ref) -->
    <Student ref="student" @click.native="show" />
    <!-- 通过父组件给子组件绑定一个自定义事件实现:子给父传递数据(第一种写法,使用@或v-on) -->
    <!-- <Student @atguigu='getStudentName' @demo='m1' />  -->
  </div>
</template>

<script>
import Student from "@/components/Student";
import School from "@/components/School";
export default {
  name: "App",
  data() {
    return {
      msg: "你好啊!",
      studentName: "",
    };
  },
  components: {
    School,
    Student,
  },
  methods: {
    getSchoolName(name) {
      console.log("App收到学校名", name);
    },
    getStudentName(name) {
      console.log("App收到学生名", name);
      this.studentName = name;
    },
    m1() {
      console.log("demo事件被触发了");
    },
    show(){
      alert(123)
    }
  },
  mounted() {
    this.$refs.student.$on("atguigu", (name) => {
      console.log("App收到学生名", name);
      console.log(this);
      this.studentName = name;
    });
  },
};
</script>

<style>
/*
   全局的样式是不需要加scoped
   全局共享
   */
.app {
  background-color: gray;
}
</style>


