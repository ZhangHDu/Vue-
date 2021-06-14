<template>
    <ul class="todo-main" v-if="todos.length !== 0">
       <item :todo="todo" :delItem="delItem" :changeCheck="changeCheck" v-for="todo in todos" :key="todo.id"/>
    </ul>
    <h1 v-else-if="isFirst">今天，也是充满希望的一天</h1>
    <h1 v-else-if="todos.length === 0">任务全部完成，可以休息了！</h1>
</template>

<script>
import item from "./item"
export default {
    name:"List",
    components:{
        item
    },
    props:{
      todos:Array,
      changeCheck:Function,
      delItem:Function,
      isFirst:Boolean
    }
}
</script>

<style>
/*main*/
.todo-main {
  margin-left: 0px;
  border: 1px solid #ddd;
  border-radius: 2px;
  padding: 0px;
}

.todo-empty {
  height: 40px;
  line-height: 40px;
  border: 1px solid #ddd;
  border-radius: 2px;
  padding-left: 5px;
  margin-top: 10px;
}

</style>