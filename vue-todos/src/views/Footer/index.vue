<template>
  <div class="todo-footer">
        <label>
          <input type="checkbox"  v-model="Check"/>
        </label>
        <span>
          <span>已完成{{done}}</span> / 全部{{this.todos.length}}
        </span>
        <button class="btn btn-danger" v-show="done" @click="delDone">清除已完成任务</button>
      </div>
</template>

<script>
export default {
  name:'Footer',
  computed:{
    Check:{
      get(){
        return this.todos.length !==0 && this.done === this.todos.length
      },
      set(val){
        this.allChange(val)
      }
    }
  },
  props:{
    todos:Array,
    done:Number,
    allChange:Function,
    delAllDone:Function
  },
  methods:{
    delDone(){
      this.delAllDone()
    }
  }
}
</script>

<style>
/*footer*/
.todo-footer {
  height: 40px;
  line-height: 40px;
  padding-left: 6px;
  margin-top: 5px;
}

.todo-footer label {
  display: inline-block;
  margin-right: 20px;
  cursor: pointer;
}

.todo-footer label input {
  position: relative;
  top: -1px;
  vertical-align: middle;
  margin-right: 5px;
}

.todo-footer button {
  float: right;
  margin-top: 5px;
}

</style>