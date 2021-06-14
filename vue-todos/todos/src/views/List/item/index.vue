<template>
   <li @mouseenter="isShow=true" @mouseleave="isShow=false">
          <label>
            <input type="checkbox" @click="Change" :checked="todo.isChecked"/>
            <span>{{todo.todo}}</span>
          </label>
          <button class="btn btn-danger" v-show="isShow" @click="del">删除</button>
        </li>
        
</template>

<script>
export default {
    name:'item',
    data(){
      return{
        isShow:false
      }
    },
    props:{
      todo:Object,
      changeCheck:Function,
      delItem:Function
    },
    methods:{
      Change(){
        this.changeCheck(this.todo.id)
      },
      del(){
        this.delItem(this.todo.id)
      }
    }
}
</script>

<style>
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
</style>