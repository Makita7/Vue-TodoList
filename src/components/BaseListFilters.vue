
<script>
    export default{
        name: 'ListFilters',
        props: { All: Object },
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
            ClearCompleted(){
                this.$emit('ClearCompleted')
            }
        },
    }
</script>

<template>
    <div class="flex">
        <div class="col count">
            {{All.filter(t => t.done === false).length}} items left
        </div>
        <div class="col flex filters">
            <button @click="getAll()">All</button>
            <button @click="getActive()">Active</button>
            <button @click="getCompleted()">Completed</button>
        </div>
        <div class="col deleteBtn">
            <button @click="ClearCompleted()">Clear Completed</button>
            <button @click="DeleteAll()">Delete All</button>
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
    button{
        background-color: #f0f8ff00;
        border-color: #f0f8ff00;
        font-weight: 600;
        transition: 0.5s;
    }
    button:hover{
        opacity: 0.6;
    }
    .deleteBtn{
        text-align: right !important;
    }
</style>