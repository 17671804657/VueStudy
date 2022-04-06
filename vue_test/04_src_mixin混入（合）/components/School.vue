<template>
  <div>
    <h2 @click="showName">学校的名称:{{ name }}</h2>
    <h2>学校的地址:{{ address }}</h2>
   
  </div>
</template>

<script>
import  {hunhe,hunhe2} from '../mixin'
export default {
  name: "Student",
  data() {
    return {
      name: "尚硅谷",
      address: '上海'
    };
  },
  mixins:[hunhe,hunhe2]
};
</script>

<style>
</style>