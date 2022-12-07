
<script>
    export default{
        name: 'ListFilters',
        props: { TodoList: Object },
        methods: {
            getAll(){
                this.$emit('getAll')
            },
            getActive(){
                this.$emit('getActive')
            },
            getCompleted(){
                this.$emit('getCompleted')
            },
            DeleteAll(){
                this.$emit('DeleteAll')
            },
        },
    }
</script>

<template>
    <div class="flex">
        <div class="col count">
            {{TodoList.filter(t => t.done === false).length}} items left
        </div>
        <div class="col flex filters">
            <button @click="getAll()">ALL</button>
            <button @click="getActive()">Active</button>
            <button @click="getCompleted()">Completed</button>
        </div>
        <div class="col">
            <button @click="DeleteAll()">
                Delete All
            </button>

        </div>
    </div>
</template>

<style>
    .col{
        width: 33%;
        text-align: center;
    }
    .filters{
        padding: 0 0.2rem;
        justify-content: space-between;
    }
    .count{
        text-align: left;
    }
</style>