<template>
    <div>
        <h2>教育背景</h2>
        <el-form>
            <el-button type="primary" v-on:click="addEducation()" class="addItem">添加</el-button>
            <div class="wrapper" v-for="(item,index) in items" :key="index">
                <el-form-item label="学校">
                    <el-input v-model="item.school"></el-input>
                </el-form-item>
                <el-form-item label="时间">
                    <el-input v-model="item.duration"></el-input>
                </el-form-item>
                <el-form-item label="学位">
                    <el-input v-model="item.degree"></el-input>
                </el-form-item>
                <el-form-item label="在校经历">
                    <el-input v-model="item.content"></el-input>
                </el-form-item>
                <i class="el-icon-error" v-on:click="removeEducation(index)"></i>
            </div>
        </el-form>
    </div>
</template>

<script>
export default {
    props: ['items'],
    methods: {
        addEducation(){
            this.items.push({
                school: '',duration: '',degree: '',content: ''
            })
        },
        removeEducation(index){
            this.items.splice(index,1)
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