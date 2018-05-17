<template>
    <div id="preview">
        <h1>年度小目标</h1>
        <el-form>
            <el-form-item>
                <el-input v-model="inputValue"></el-input>
            </el-form-item>
        </el-form>        
        <ul>
            <previewchild 
            v-for="(item,index) in list"
            :key="index"
            :content = "item"
            :index = "index"
            @delete = "deleteList">
            </previewchild>
        </ul>
        <el-button type="success" @click="handleSubmit">添加年度目标</el-button>
    </div>
</template>

<script>
import Previewchild from './Previewchild'
export default {
    components: {
        'previewchild': Previewchild
    },
    data() {
        return{
            inputValue: '',
            list: []
        }
    },
    methods: {
        handleSubmit() {
            if(this.inputValue){
                this.list.push(this.inputValue)
                this.inputValue = ''
            }
            
        },
        deleteList(index){
            this.list.splice(index,1)
        }
    }
}
</script>

<style lang="scss">
    #preview{
        padding: 32px;
        > h1{
        text-align: center;
        }
    }
</style>

