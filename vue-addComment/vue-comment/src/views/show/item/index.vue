<template>
  <li class="list-group-item">
            <div class="handle">
              <a href="javascript:;" @click="delItem">删除</a>
            </div>
            <p class="user"><span >{{msg.user}}</span><span>说:</span></p>
            <p class="centence">{{msg.comment}}</p>
          </li>
</template>

<script>
export default {
    name:'item',
    props:{
        msg:Object,
        del:Function
    },
    methods:{
        delItem(){
            this.del(this.msg.id)
        }
    }
}
</script>

<style>
li {
  transition: .5s;
  overflow: hidden;
}

.handle {
  width: 40px;
  border: 1px solid #ccc;
  background: #fff;
  position: absolute;
  right: 10px;
  top: 1px;
  text-align: center;
}

.handle a {
  display: block;
  text-decoration: none;
}
.user {
  font-size: 22px;
}
</style>