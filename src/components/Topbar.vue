<template>
    <div id="topbar">
        <div class="logo">
            VueResumer
        </div>
        <div class="actions">
            <el-button type="primary" @click="preview">预览</el-button>
        </div>
    </div>
</template>

<script>
export default {
    methods: {
        preview () {
            this.$emit('preview')
        }

    }
}
</script>


<style lang="scss">
    #topbar{
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 16px 32px;
        font-size: 20px;
    }
</style>
