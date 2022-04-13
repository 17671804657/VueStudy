<template>
   <div class="school">
     <h2>学校名称:{{  name }}</h2>
     <h2>学校地址: {{ address }}</h2>
   </div>
</template>

<script>
export default {
  name: "School",
  data(){
    console.log(this);
    return {
       name: 'wust university',
       address: '武汉科技大学'
    }
  },
  mounted() {
    this.$bus.$on('hello',(data)=>{
      console.log('我是School组件，收到了数据',data);
    })
  },
  beforeDestroy() {
    this.$bus.$off('hello')
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


