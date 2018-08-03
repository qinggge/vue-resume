<template>
    <div id="topbar">
        <div class="logo">
            VueResumer
        </div>
        <div class="actions">
            <el-button type="primary">登录</el-button>
            <el-button>注册</el-button>
            <el-button v-on:click="preview()">预览</el-button>
        </div>
    </div>
</template>

<script>
export default {
    methods:{
        preview(){
            console.log(1)
            this.$emit('preview')
        }
    }
}
</script>


<style lang="scss">
#topbar {
  display: flex;
  justify-content: space-between;
  padding: 16px;
  font-size: 20px;
  align-items: center;
  color: rgb(19, 100, 206);
}
</style>