<template>
    <div id="topbar">
        <div class="logo">
            VueResumer
        </div>
        <div class="actions">
            <span style="font-size:14px;">注意：请在填写完相关信息之后，点击预览，打开打印设置进行保存！Window：CTRL + P || Mac：Command + P</span>
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