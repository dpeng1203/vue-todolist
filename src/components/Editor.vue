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
                <h2>个人经历</h2>
                <el-form>
                    <div class="container" v-for="(work,index) in workHistory">
                
                    <el-form-item label="时间段">
                        <el-input v-model="work.company"></el-input>
                    </el-form-item>
                    <el-form-item label="记忆犹新记录">
                        <el-input v-model="work.content"></el-input>
                    </el-form-item>
                    <el-button type="danger" icon="el-icon-delete" circle @click="removeWorkHistory(index)" class= "el-icon-delete"></el-button>
                        <hr>
                    </div>
                </el-form>
                <el-button type="success" @click="addWorkHistory">添加个人经历</el-button>
            </li>
            <li :class="{active: currentTab === 2}">
                <h2>成长经历</h2>
                <el-form>
                    <el-form-item label="高中">
                        <el-input v-model="profile.name"></el-input>
                    </el-form-item>
                    <el-form-item label="大学">
                        <el-input v-model="profile.city"></el-input>
                    </el-form-item>
                    <el-form-item label="硕士"> 
                        <el-input v-model="profile.birth"></el-input>
                    </el-form-item>
                </el-form>
            </li>
            <li :class="{active: currentTab === 3}">
                <h2>家庭情况</h2>
                <el-form>
                    <el-form-item label="父亲">
                        <el-input v-model="profile.name"></el-input>
                    </el-form-item>
                    <el-form-item label="母亲">
                        <el-input v-model="profile.city"></el-input>
                    </el-form-item>
                    <el-form-item label="兄弟姐妹"> 
                        <el-input v-model="profile.birth"></el-input>
                    </el-form-item>
                </el-form>
            </li>
            <li :class="{active: currentTab === 4}">
                <h2>获奖情况</h2>
                <el-form>
                    <el-form-item label="时间">
                        <el-input v-model="profile.name"></el-input>
                    </el-form-item>
                    <el-form-item label="事件">
                        <el-input v-model="profile.city"></el-input>
                    </el-form-item>
                    <el-form-item label="感言"> 
                        <el-input v-model="profile.birth"></el-input>
                    </el-form-item>
                </el-form>
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
export default {
    components: { ProfileEditor },
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
            ]
        }
    },
    methods: {
        addWorkHistory(){
            this.workHistory.push({
                company: '',content: ''
            })
        },
        removeWorkHistory(index){
            this.workHistory.splice(index,1)
        }
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
