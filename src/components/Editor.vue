<template>
    <div id = "editor">
        <nav>
            <ol>
                <li v-for="i in [0,1,2,3,4,5]"
                    :class="{active: currentTab === i}"
                    @click="currentTab = i">
                    <svg class="icon">
                    <use :xlink:href="`#icon-${icons[i]}`"></use></svg>
                </li>
            </ol>
        </nav>
        <ol class="panes">
            <li :class="{active: currentTab === 0}">
                <ProfileEditor :profile='profile'/>
            </li>
            <li :class="{active: currentTab === 1}">
                <ArrayEditor :items = "workHistory" 
                             :labels="{company: '公司',content: '工作内容'}" 
                             title = "工作经历"/>
            </li>
            <li :class="{active: currentTab === 2}">
                <ArrayEditor :items = "studyHistory" 
                             :labels="{school: '公司',duration: '工作内容', degree: '学位'}" 
                             title = "学习经历"/>
            </li>
            <li :class="{active: currentTab === 3}">
                <ArrayEditor :items = "projects" 
                             :labels="{name: '项目名称',content: '工作内容'}" 
                             title = "项目经历"/>

            </li>
            <li :class="{active: currentTab === 4}">
                <ArrayEditor :items = "awards" 
                             :labels="{name: '项目奖励'}" 
                             title = "获奖情况"/>

            </li>
            <li :class="{active: currentTab === 5}">
                <h2>联系方式</h2>
                <el-form>
                    <el-form-item label="QQ">
                        <el-input v-model="profile.name"></el-input>
                    </el-form-item>
                    <el-form-item label="微信">
                        <el-input v-model="profile.city"></el-input>
                    </el-form-item>
                    <el-form-item label="电话"> 
                        <el-input v-model="profile.birth"></el-input>
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
    components: { ProfileEditor, ArrayEditor },
    data() {
        return{
            currentTab: 0,
            icons: ['shenfenzheng','work0','book','heart','goldcup','phone'],
            profile: {
                name: '',
                city: '',
                birth: ''
            },
            workHistory: [
                {company: '',content: ''}
            ],
            studyHistory: [
                {school: '',duration: '',degree: ''}
            ],
            projects: [
                {name: '',content: ''}
            ],
            awards: [
                {name: ''}
            ]
        }
    },
    methods: {
        
    },
    created(){
        setTimeout(() => {
            console.log(this.profile)
        }, 10000);
    }
}
</script>


<style lang = "scss">
    #editor{
        border: 1px solid red;
        min-height: 100px;
        display: flex;
        > nav{
            background: #000;
            width: 80px;
        
            > ol > li{
                padding: 16px 0;
                text-align: center;
                > .icon{
                    width: 24px;
                    height: 24px;
                    fill: #fff;
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
            .container{
                position: relative;
                .el-icon-delete{
                    position: absolute;
                    top: 0;
                    right: 0;
                }
            }
            > li{
                height: 100%;
                overflow: auto;
                display: none;
                padding: 16px;
                &.active{
                    display: block;
                }
            }
        }
    }
</style>
