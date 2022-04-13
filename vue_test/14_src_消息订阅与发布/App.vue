<template>
  <div class="app">
    <h1>{{msg}}</h1>
    <School/>
    <Student/>
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


