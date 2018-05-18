<template>
    <div id="preview">
        <h1>Resume</h1>
        <section>
            <H2>个人信息</H2>
            <hr style="height:3px;border:none;border-top:3px double red;" />
            <p>{{resume.profile.name || '请填写名字'}} | {{resume.profile.city || '请填写城市'}} | {{resume.profile.birth || '请填写出生年月'}}</p>
        </section>
        <section v-if="filter(resume.workHistory).length > 0">
            <h2>工作经历</h2>
            <hr style="height:3px;border:none;border-top:3px double red;" />
            <ul>
                <li v-for="work in filter(resume.workHistory)">
                    公司: {{work.company}}<br>
                    工作内容：{{work.content}}
                </li>
            </ul>
        </section>
        
        <section v-if="filter(resume.studyHistory).length > 0">
            <h2>学习经历</h2>
            <hr style="height:3px;border:none;border-top:3px double red;" />
            <ul>
                <li v-for="study in filter(resume.studyHistory)">
                    学校：{{study.school}}<br>
                    时间段：{{study.duration}}<br>
                    学位：{{study.degree}}
                </li>
            </ul>
        </section>
        <section v-if="filter(resume.projects).length > 0">
            <h2>项目经历</h2>
            <hr style="height:3px;border:none;border-top:3px double red;" />
            <ul>
                <li v-for="project in filter(resume.projects)">
                    项目名称：{{project.name}}<br>
                    项目内容：{{project.content}}
                </li>
            </ul>
        </section>
        <section v-if="filter(resume.awards).length > 0">
            <h2>获奖情况</h2>
            <hr style="height:3px;border:none;border-top:3px double red;" />
            <ul>
                <li v-for="work in filter(resume.awards)">
                    获奖感言：{{work.name}}
                </li>
            </ul>
        </section>
        <section>
            <h2>联系方式</h2>
            <hr style="height:3px;border:none;border-top:3px double red;" />
            <p>{{resume.contacts.qq || '请填写qq'}} | {{resume.contacts.wechat || '请填写微信'}} | {{resume.contacts.telephone || '请填写电话'}}</p>
        </section>

    </div>
</template>

<script>
export default {
    props: ['resume'],
    methods: {
        filter(array){
            return array.filter(item=> !this.isEmpty(item))
        },
        isEmpty(object){
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

<style lang="scss">
    #preview{
        overflow: auto;
        padding: 32px;
        > h1{
            color: chartreuse;
            text-align: center;
        }
        > section{
            padding: 16px;
            > h2, p, li{
                padding: 8px;
            }
            > h2{
                color: chocolate;
            }
        }
    }
</style>

