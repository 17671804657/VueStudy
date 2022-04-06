<template>
  <div>
    <School/>
    <hr>
    <Student/>
    
  </div>
</template>

<script>
import School from "./components/School.vue"
import Student from "./components/Student";
export default {
  name: "App",
  components: { Student,School },
};
</script>

<style>
</style>