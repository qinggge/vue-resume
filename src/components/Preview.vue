<template>
    <div id="preview">
        <h1>{{resume.profile.name || '请输入姓名'}}</h1>
        <p>{{resume.profile.city || '请输入城市'}} | {{resume.profile.birth || '请输入出生年月'}}</p>
        <hr>
        <section v-if="filter(resume.project)">
            <h2>项目</h2>
            <ul>
                <li v-for="project in filter(resume.project)" :key="project.name">
                    <h2>{{project.name}}</h2>
                    <p>{{project.content}}</p>
                </li>
            </ul>
        </section>
        <hr>
        <section v-if="filter(resume.workExp)">
            <h2>工作经历</h2>
            <ul>
                <li v-for="workExp in filter(resume.workExp)" :key="workExp.name">
                    <h2>{{workExp.company}} | {{workExp.duration}}</h2>
                    <p>{{workExp.content}}</p>
                </li>
            </ul>
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

</style>