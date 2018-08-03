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
                <ProfileEditor v-bind:profile="profile"/> 
            </li>
            <li v-bind:class="{active: currentTab === 1}">
                <WorkExp v-bind:workExprience="workExprience    "/>
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
import ProfileEditor from './ProfileEditor'
import WorkExp from './WorkExp'
export default {
    components: { ProfileEditor,WorkExp },
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