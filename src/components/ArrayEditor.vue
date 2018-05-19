<template>
    <div>
        <h2>{{title}}</h2>
        <el-form>
            <div class="container" v-for="(work,index) in items" :key="index">
            <el-form-item v-for="key in keys" :label="labels[key] || key" :key="key">
                <el-input v-model="work[key]"></el-input>
            </el-form-item>
            <div @click="removeitems(index)" class= "icon-delete">
              <i class="el-icon-delete" ></i>
            </div>
            <hr>
            </div>
            <el-button type="success" @click="additems">添加一项</el-button>
        </el-form>
    </div>
</template>

<script>
export default {
    props: ['items','labels','title'],
    computed: {
        keys(){
            return Object.keys(this.items[0])
        }
    },
    methods: {
        additems(){
            const empty = {}
            this.keys.map((key)=>{
                empty[key] = ''
            })
            this.items.push(empty)
        },
        removeitems(index){
            this.items.splice(index,1)
        }
    }
    
    
}
</script>
