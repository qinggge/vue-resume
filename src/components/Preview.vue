<template>
    <div id="preview">
        <section>
            <h1>{{resume.profile.name || '请输入姓名'}}</h1>
            <h3>{{resume.profile.city || '请输入城市'}} | {{resume.profile.birth || '请输入出生年月'}}</h3>
        </section>
        <hr>
        <section v-if="filter(resume.workExp)">
            <h1>工作经历</h1>
            <ul>
                <li v-for="workExp in filter(resume.workExp)" :key="workExp.name">
                    <h3>{{workExp.company}} | {{workExp.duration}}</h3>
                    <p>{{workExp.content}}</p>
                </li>
            </ul>
        </section>
        <hr>
        <section v-if="filter(resume.project)">
            <h1>项目经验</h1>
            <ul>
                <li v-for="project in filter(resume.project)" :key="project.name">
                    <h3>{{project.name}}</h3>
                    <p>{{project.content}}</p>
                </li>
            </ul>
        </section>
        <hr>
        <section v-if="filter(resume.education)">
            <h1>教育背景</h1>
            <ul>
                <li v-for="education in filter(resume.education)" :key="education.name">
                    <h3>{{education.school}} | {{education.duration}} | {{education.degree}}</h3>
                </li>
            </ul>
        </section>
        <hr>
        <section>
            <h1>联系方式</h1>
            <p>QQ：{{resume.contact.QQ || '请输入您的QQ'}} | 微信：{{resume.contact.wechat || '请输入您的微信'}}</p>
            <p>手机：{{resume.contact.tel || '请输入您的手机号码'}} | 邮箱：{{resume.contact.email || '请输入您的邮箱地址'}}</p>
        </section>
    </div>
</template>

<script>
export default {
    props: ['resume'],
    methods:{
        filter(array){ // 找出非空对象
            return array.filter( (item)=> !this.isEmpty(item) )
        },
        isEmpty(object){ // 只要有一个value不是falsy，就返回false
            let empty = true
            for(let key in object){
                if(object[key]){
                    empty = false
                    break
                }
            }
            return empty
        }
    }
}
</script>

<style>
    #preview section{
        margin: 8px 16px 16px 16px;
    }
    #preview section h1{
        margin: 16px 0 8px;
        padding: 0;
    }
    #preview section h3{
        margin: 8px 0;
    }
    #preview hr{
        width: 90%;
        border: none;
        height: 1px;
    }
</style>