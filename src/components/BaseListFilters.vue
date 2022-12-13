
<script>
    export default{
        name: 'ListFilters',
        props: {
            All: Object,
            DarkMode: Boolean,
        },
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
            <p>{{All.filter(t => t.done === false).length}} items left</p>
        </div>
        <div class="col flex filters">
            <button @click="getAll()" :class="{DarkMode: DarkMode}" >All</button>
            <button @click="getActive()" :class="{DarkMode: DarkMode}" >Active</button>
            <button @click="getCompleted()" :class="{DarkMode: DarkMode}" >Completed</button>
        </div>
        <div class="col deleteBtn">
            <button @click="ClearCompleted()" :class="{DarkMode: DarkMode}" >Clear Completed</button>
            <button @click="DeleteAll()" :class="{DarkMode: DarkMode}" >Delete All</button>
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
        color: rgb(0, 0, 0);
        opacity: 0.6;
        transition: 1s ease-in-out;
    }
    button:hover{
        opacity: 1;
        color: hsl(220, 98%, 61%);
    }
    .DarkMode{
        color: hsl(234, 39%, 85%);
    }
    .deleteBtn{
        text-align: right !important;
    }
</style>