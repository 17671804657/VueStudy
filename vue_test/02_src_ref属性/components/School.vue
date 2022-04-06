<template>
  <div class="demo">
      <h2>学校的名称:{{name}}</h2>
      <h2>学校的地址:{{address}}</h2>
  </div>
</template>

<script>
export default {
    name:'School',
    data() {
        return {
            name:'张三',
            address:'上海'
        }
    },
}
</script>

<style>
    .demp{
        background-color: #bfa;
    }
</style>