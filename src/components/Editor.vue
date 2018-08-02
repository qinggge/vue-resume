<template>
    <div id="editor">
        <nav>
            <ol>
                <li v-for="i in [0,1,2,3,4]" 
                    :key="i"
                    v-bind:class="{active: currentTab === i}" 
                    v-on:click="currentTab = i"
                    >
                    <svg class="icon" aria-hidden="true">
                        <use v-bind:xlink:href="`#icon-${icons[i]}`"></use>
                    </svg>
                </li>
            </ol>
        </nav>
        <ol class="panes">
            <li v-bind:class="{active: currentTab === 0}">
                <h2>个人信息</h2>
                <el-form>
                    <el-form-item label="姓名">
                        <el-input v-model="profile.name"></el-input>
                    </el-form-item>
                    <el-form-item label="城市">
                        <el-input v-model="profile.city"></el-input>
                    </el-form-item>
                    <el-form-item label="出生年月">
                        <el-input v-model="profile.birth"></el-input>
                    </el-form-item>
                </el-form>
            </li>
            <li v-bind:class="{active: currentTab === 1}">
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
            </li>
            <li v-bind:class="{active: currentTab === 2}">
                <h2>项目经历</h2>
            </li>
            <li v-bind:class="{active: currentTab === 3}">
                <h2>教育背景</h2>
            </li>
            <li v-bind:class="{active: currentTab === 4}">
                <h2>联系方式</h2>
            </li>
        </ol>
    </div>
</template>

<script>
export default {
    data(){
        return {
            currentTab: 0,
            icons: ['IDcard','centericjob','project','book','tel'],
            profile: {
                name: '',
                city: '',
                birth: ''
            },
            workExprience: [
                {company:'',content:''}
            ]
        }
    },
    methods: {
        addWorkExprience(){
            this.workExprience.push({
                company: '',content: ''
            })
            console.log(this.workExprience)
        },
        removeWorkExprience(index){
            this.workExprience.splice(index,1)
        }
    },
    created(){
        
    }
}
</script>


<style lang="scss">
#editor {
    display: flex;
    min-height: 100px;
    > nav {
        background: black;
        width: 88px;
        > ol > li {
            padding: 16px 0;
            text-align: center;
            > .icon {
                width: 32px;
                height: 32px;
                fill: white;
            }
            &.active{
                background: white;
                > .icon{
                    fill: black;
                }
            }
        }
    }
    > .panes{
        flex: 1;
        > li{
            display: none;
            padding: 24px;
            &.active{
                display: block;
                height: 100%;
                overflow: auto;
                > .el-form{
                    position: relative;
                    > .addExp{
                        position: absolute;
                        right: 30px;
                        top: -10px;
                        z-index: 1;
                    }
                }
            }
        }
        .wrapper{
            position: relative;
            > i{
                position: absolute;
                top: 0;
                right: 0;
            }
        }
    }
}
</style>