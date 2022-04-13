<template>
  <div class="school">
    <h2>学校名称:{{ name }}</h2>
    <h2>学校地址: {{ address }}</h2>
  </div>
</template>

<script>
import pubsub from 'pubsub-js'
export default {
  name: "School",
  data(){
    console.log(this);
    return {
       name: 'wust university',
       address: '武汉科技大学'
    }
  },
 methods: {
   demo(msgName,data){
     console.log('hello消息收到了',msgName,data)
    }
 },
  mounted() {
    this.pubId = pubsub.subscribe('hello',this.demo)
  },
  beforeDestroy() {
    // this.$bus.$off('hello')
    pubsub.unsubscribe(this.pubId)
  },
}
</script>

<style scoped>
/*scoped代表局部的*/
.school {
  background: skyblue;
  padding: 10px;
}
</style>


