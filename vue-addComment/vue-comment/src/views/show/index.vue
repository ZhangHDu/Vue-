<template>
   <div class="col-md-8">
        <h3 class="reply">评论回复：</h3>
        <h2 style='display: none'>暂无评论，点击左侧添加评论！！！</h2>
        <ul class="list-group">
          <Item v-for="msg in msgs" :del="del" :key="msg.id" :msg="msg"/>
        </ul>
      </div>
</template>

<script>
import Item from './item'
export default {
    name:'show',
    components:{
        Item
    },
    data(){
        return{
            msgs:[
                {id:1,user:'小张',comment:'Vue真好玩'},
                {id:2,user:'小吴',comment:'Vue真好玩'},
                {id:3,user:'小王',comment:'Vue真好玩'},
            ]
        }
    },
    methods:{
        addComment(user,comment){
            this.msgs.unshift({
                id:Date.now(),
                user,
                comment
            })
        },
        del(id){
            this.msgs = this.msgs.filter((msg)=>msg.id !== id)
        }
    },
    mounted(){
        //绑定事件
        this.$bus.$on('addComment',this.addComment)
        this.$bus.$on('delComment',this.delComment)
    },
    beforeDestroy(){
        //解绑事件
        this.$bus.$off('addComment',this.addComment)
         this.$bus.$off('delComment',this.delComment)
    }
}
</script>

<style>
.reply {
  margin-top: 0px;
}
.list-group-item .centence {
  padding: 0px 50px;
}

</style>