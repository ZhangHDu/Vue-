<template>
   <div class="col-md-4">
        <form class="form-horizontal">
          <div class="form-group">
            <label>用户名</label>
            <input type="text" class="form-control" placeholder="用户名" v-model="user">
          </div>
          <div class="form-group">
            <label>评论内容</label>
            <textarea class="form-control" rows="6" placeholder="评论内容" v-model="comment"></textarea>
          </div>
          <div class="form-group">
            <div class="col-sm-offset-2 col-sm-10">
              <button type="button" @click="up" class="btn btn-default pull-right">提交</button>
            </div>
          </div>
        </form>
      </div>
</template>

<script>
export default {
    name:"Add",
    data(){
      return{
        user:"",
        comment:""
      }
    },
    methods:{
      up(){
       const {user,comment} = this
       if(!user||!comment){
         alert('请输入内容')
         return
       }
       this.$bus.$emit("addComment",user,comment)
       this.user = ''
       this.comment = ''
      }
    }
}
</script>

<style>

</style>