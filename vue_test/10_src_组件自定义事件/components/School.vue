<template>
   <div class="school">
     <h2>学校名称:{{  name }}</h2>
     <h2>学校地址: {{ address }}</h2>
     <button @click="sendSchoolName">吧学校名给App</button>
   </div>
</template>

<script>
export default {
  name: "School",
  props:['getSchoolName'],
  data(){
    console.log(this);
    return {
       name: 'wust university',
       address: '武汉科技大学'
    }
  },
  methods: {
    sendSchoolName(){
      this.getSchoolName(this.name)
    }
  },
}
</script>

<style scoped>
   /*scoped代表局部的*/
  .school{
    background: skyblue;
    padding: 10px;
  }
</style>


