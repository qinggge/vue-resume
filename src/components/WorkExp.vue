<template>
    <div>
        <h2>工作经历</h2>
        <el-form>
            <el-button type="primary" v-on:click="addWorkExprience()" class="addExp">添加</el-button>
            <div class="wrapper" v-for="(work,index) in workExprience" :key="index">
                <el-form-item label="公司">
                    <el-input v-model="work.company"></el-input>
                </el-form-item>
                <el-form-item label="工作内容">
                    <el-input v-model="work.content"></el-input>
                </el-form-item>
                <i class="el-icon-error" v-on:click="removeWorkExprience(index)"></i>
            </div>
        </el-form>
    </div>
</template>

<script>
export default {
    props: ['workExprience'],
    methods: {
        addWorkExprience(){
            this.workExprience.push({
                company: '',content: ''
            })
        },
        removeWorkExprience(index){
            this.workExprience.splice(index,1)
        }
    }
}
</script>

<style lang="scss">
.el-form{
    position: relative;
        .addExp {
        position: absolute;
        right: 30px;
        top: -10px;
        z-index: 1;
    }
}
</style>
