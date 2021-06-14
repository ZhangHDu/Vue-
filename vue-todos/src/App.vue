<template>
   <div class="todo-container">
    <div class="todo-wrap">
      <Header :addtodo="addtodo" />
      <List :todos="todos" :isFirst="isFirst" :changeCheck="changeCheck" :delItem="delItem"/>
      <Footer :todos="todos" :delAllDone="delAllDone" :done="done" :allChange="allChange"/>
    </div>
  </div>
</template>

<script>
import Header from './views/Header'
import List from './views/List'
import Footer from './views/Footer'
export default {
  name:"App",
  components:{
    Header,
    List,
    Footer,
  },
  data(){
    return{
      todos:[],
      // 默认值第一次进来为true
      isFirst:true
    }
  },
  methods:{
    //添加任务
    addtodo(todo){
      this.todos.unshift({
        id:Date.now(),
        todo:todo,
        isChecked:false
      }),
      // 触发事件后把isFirst改为false
      this.isFirst=false
    },
    //修改任务状态
    changeCheck(id){
      const todo = this.todos.find((todo)=>todo.id === id)
      todo.isChecked = !todo.isChecked
    },
    //修改底部状态
    allChange(Check){
      this.todos.forEach((todo)=>{
        todo.isChecked = Check
      })
    },
    //删除单个任务
    delItem(id){
      this.todos = this.todos.filter((todo)=>todo.id !== id)
    },
    //删除已完成任务
    delAllDone(){
      this.todos = this.todos.filter((todo)=> !todo.isChecked)
    }
  },
  //计算已完成的任务数量
  computed:{
    done(){
      return this.todos.reduce((p,c)=>{
        return p + (c.isChecked?1:0)
      },0)
    }
  }
}
</script>

<style>

/*app*/
.todo-container {
  width: 600px;
  margin: 0 auto;
}
.todo-container .todo-wrap {
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 5px;
}
</style>