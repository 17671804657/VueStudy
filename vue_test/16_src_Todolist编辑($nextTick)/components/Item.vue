<template>
  <li>
    <label>
      <!--这里勾选和取消勾选可以使用change和click作为事件处理-->
      <input type="checkbox" :checked="todo.done" @change="handleCheck(todo.id)" />
      <!--v-model数据的双向绑定，checkbox使用v-model来双向绑定其是否被勾选,也可以实现效果但不推荐(因为其实修改了props中的数据)-->
      <!--这里修改了从List修改过来的props,这里的不允许改是浅层次，就是如果props是一个对象则这个修改这个对象的某一个属性vue是放行的-->
      <!-- <input type="checkbox" v-model="todo.done"/>-->
      <span v-show="!todo.isEdit">{{  todo.title }}</span>
      <input 
        type="text" 
        :value="todo.title"
        v-show="todo.isEdit" 
        @blur="handleBlur(todo,$event)"
        ref="inputTitle"/>
    </label>

    <button class="btn btn-danger" @click="handleDelete(todo.id)">删除</button>
    <button  v-show="!todo.isEdit" class="btn btn-edit" @click="handleEdit(todo)">编辑</button>
  </li>
</template>

<script>
import pubsub from "pubsub-js";
export default {
  name: "Item",
  //声明接收todo
  props: ["todo"],
  methods: {
    handleCheck(id) {
      //事件总线
      this.$bus.$emit("checkTodo", id);
    },
    handleDelete(id) {
      if (confirm(`确定删除编号为${id}的todo吗`)) {
        // console.log(id);
        //事件总线
        // this.$bus.$emit('deleteTodo',id);
        pubsub.publish("deleteTodo", id);
      }
    },
    //编辑
    handleEdit(todo) {
      if (todo.hasOwnProperty('isEdit')) {
        todo.isEdit = true
      }else{
        console.log('@');
         this.$set(todo, 'isEdit', true);
      }
      //自动获取焦点
      //this.$refs.inputTitle.focus(); //此时你这行代码执行了，但是注意vue并没有重新解析模版(input并没有出现在页面上，dom节点并没有被更新)，它一定要等这个回调函数执行完之后才会去重新渲染模版
      //使用nextTick来解决
      this.$nextTick(() => {
        //这里的回调函数注意是在dom节点被更新之后才会运行的
        this.$refs.inputTitle.focus();
      })
      console.log(todo);
    },
    //失去焦点回调（真正执行修改逻辑）
    handleBlur(todo, e){
      todo.isEdit = false; //注意我在这里确保你身上一定存在isEdit属性
      if(!e.target.value.trim()) {
        alert('输入不能为空');
        return;
      }
      this.$bus.$emit('updateTodo', todo.id, e.target.value);
    }
  },
};
</script>

<style scoped>
/*item*/
li {
  list-style: none;
  height: 36px;
  line-height: 36px;
  padding: 0 5px;
  border-bottom: 1px solid #ddd;
}

li label {
  float: left;
  cursor: pointer;
}

li label li input {
  vertical-align: middle;
  margin-right: 6px;
  position: relative;
  top: -1px;
}

li button {
  float: right;
  display: none;
  margin-top: 3px;
}

li:before {
  content: initial;
}

li:last-child {
  border-bottom: none;
}

li:hover {
  background: #ddd;
}

li:hover button {
  display: block;
}
</style>
