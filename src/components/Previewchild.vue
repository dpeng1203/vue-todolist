<template>
    <div>
        <h2><li class="elememt" @click=handleDelete>{{content}}</li></h2>
        <hr>
    </div>
</template>

<script>
export default {
    props: ['content','index'],
    methods: {
        handleDelete() {
            this.$emit('delete',this.index)
        }
    }
}
</script>

<style>
    li{
        padding: 5px 20px;
    }
</style>

