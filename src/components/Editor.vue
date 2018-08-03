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
                <ProfileEditor v-bind:profile="resume.profile"/> 
            </li>
            <li v-bind:class="{active: currentTab === 1}">
                <ArrayEditor v-bind:items="resume.workExp" v-bind:labels="{company:'公司',duration:'工作年限',content:'工作内容'}" v-bind:title="'工作经历'"/>
            </li>
            <li v-bind:class="{active: currentTab === 2}">
                <ArrayEditor v-bind:items="resume.project" v-bind:labels="{name:'项目名称',content:'工作内容'}" v-bind:title="'项目经验'"/>
            </li>
            <li v-bind:class="{active: currentTab === 3}">
                <ArrayEditor v-bind:items="resume.education" v-bind:labels="{school:'学校',duration:'时间',degree:'学位'}" v-bind:title="'教育背景'"/>
            </li>
            <li v-bind:class="{active: currentTab === 4}">
                <h2>联系方式</h2>
                <el-form>
                    <el-form-item label="QQ">
                        <el-input v-model="resume.contact.QQ"></el-input>
                    </el-form-item>
                    <el-form-item label="微信">
                        <el-input v-model="resume.contact.wechat"></el-input>
                    </el-form-item>
                    <el-form-item label="手机">
                        <el-input v-model="resume.contact.tel"></el-input>
                    </el-form-item>
                    <el-form-item label="邮箱">
                        <el-input v-model="resume.contact.email"></el-input>
                    </el-form-item>
                </el-form>
            </li>
        </ol>
    </div>
</template>

<script>
import ProfileEditor from './ProfileEditor'
import ArrayEditor from './ArrayEditor'
export default {
    components: { ProfileEditor,ArrayEditor},
    props: ['resume'],
    data(){
        return {
            currentTab: 0,
            icons: ['IDcard','centericjob','project','book','tel']
        }
    },
    methods: {
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