<template>
    <div id="preview">
        <section class="info">
            <h2 class="title">个人信息</h2>
            <p class="description">Personal Infomation</p>
            <h1>{{resume.profile.name || '请输入姓名'}}</h1>
            <p>{{resume.profile.sex || '请输入性别' }} | {{resume.profile.city || '请输入城市'}} | {{resume.profile.birth || '请输入出生年月'}}</p>
        </section>
        <section v-if="filter(resume.workExp)" class="exp">
            <h2 class="title">工作经历</h2>
            <p class="description">Work Experience</p>
            <dl v-for="workExp in filter(resume.workExp)" :key="workExp.name">
                <dt>{{workExp.company}} | {{workExp.position}} | {{workExp.duration}}</dt>
                <dd>{{workExp.content}}</dd>
            </dl>
        </section>
        <section v-if="filter(resume.project)" class="projects">
            <h2 class="title">项目经验</h2>
            <p class="description">Projects</p>
            <dl v-for="project in filter(resume.project)" :key="project.name">
                <dt>{{project.name}}</dt>
                <dd>{{project.content}}</dd>
            </dl>
        </section>
        <section v-if="filter(resume.education)" class="educations">
            <h2 class="title">教育背景</h2>
            <p class="description">Education</p>
            <dl v-for="education in filter(resume.education)" :key="education.name">
                <dt>{{education.school}} | {{education.duration}} | {{education.degree}}</dt>
                <dd>{{education.content}}</dd>
            </dl>
        </section>
        <section>
            <h2 class="title">联系方式</h2>
            <p class="description">Communication</p>
            <p>QQ：{{resume.contact.QQ}} | 微信：{{resume.contact.wechat}}</p>
            <p>手机：{{resume.contact.tel}} | 邮箱：{{resume.contact.email}}</p>
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
var AV = require('leancloud-storage')
</script>

<style>
#preview{
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol";  
    background: rgb(233, 228, 228);
    border: 1px solid grey;
    box-shadow: 0 0 10px 1px grey;
}
#preview section{
    margin: 8px 16px 16px 16px;
}
#preview section h1{
    font-size: 20px;
    font-weight: bold;
}
section .title {
    font-size: 20px;
    padding: 8px 0px 0px;
    font-weight: normal;
}
section .description {
    font-size: 14px;
    color: teal;
    margin-bottom: 16px;
    border-bottom: 2px dashed teal;
    font-style: italic;
    line-height: 1.5;
    font-weight: 400;
}
#preview section {
    padding: 24px 32px 0px 32px;
}
#preview dl{

}
#preview dl dt {
    color: #044D22;
    font-weight: bold;
    margin-top: 16px;
    margin-bottom: 8px;
    font-size: 16px;
}
#preview dl dd {
    text-indent: 2em;
}
</style>