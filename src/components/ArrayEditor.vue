<template>
    <div>
        <h2>{{title}}</h2>
        <el-form>
            <el-button type="primary" v-on:click="addWorkExprience()" class="addItem">添加</el-button>
            <div class="wrapper" v-for="(work,index) in items" :key="index">
                <el-form-item v-for="key in keys" v-bind:label="labels[key] || key" :key="key">
                    <el-input v-model="work[key]"></el-input>
                </el-form-item>
                <i class="el-icon-error" v-on:click="removeWorkExprience(index)"></i>
            </div>
        </el-form>
    </div>
</template>

<script>
export default {
    props: ['items','labels','title'],
    computed: {
        keys(){
            return Object.keys(this.items[0])
        }
    },
    methods: {
        addWorkExprience(){
            const empty = {}
            this.keys.map((key)=>{
                empty[key] = ''
            })
            this.items.push(empty)
        },
        removeWorkExprience(index){
            if(this.items.length === 1){
                console.log('不能再删啦！！！！！')
            }else{
                this.items.splice(index,1)
            }
        }
    }
}
</script>

<style lang="scss">
.el-form{
    position: relative;
        .addItem {
        position: absolute;
        right: 30px;
        top: -10px;
        z-index: 1;
    }
}
</style>