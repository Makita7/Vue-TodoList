
<!-- the input should be posted to list with enter key -->
<script>
    export default{
        props: {
            newTodo: String,
        },
        methods: {
            AddTodo(){
                this.$emit('AddTodo')
            }
        }
    }
</script>

<template>

</template>

<style scoped>
    input{
        width: 100%;
        border-radius: 5px;
        border-color: rgba(240, 248, 255, 0);
        height: 3rem;
        margin: 2rem 0 1rem 0;
        font-size: 1.4rem;
        padding: 0rem 2rem;
        box-sizing: border-box;
    }
</style>