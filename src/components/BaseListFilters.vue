
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
            <button aria-label="see all items" @click="getAll()" :class="{DarkMode: DarkMode}" >All</button>
            <button aria-label="see only active items" @click="getActive()" :class="{DarkMode: DarkMode}" >Active</button>
            <button aria-label="see only completed items" @click="getCompleted()" :class="{DarkMode: DarkMode}" >Completed</button>
        </div>
        <div class="col deleteBtn">
            <button aria-label="clear completed items" @click="ClearCompleted()" :class="{DarkMode: DarkMode}" >Clear Completed</button>
            <button aria-label="clear all items in list" @click="DeleteAll()" :class="{DarkMode: DarkMode}" >Delete All</button>
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
    @media (max-width: 767px){
        .deleteBtn{
            display: block;
        }
        button{
            padding: 0.3rem 0;
        }
        .filters{
            display: grid;
        }
        .deleteBtn{
            display: grid;
        }
        .count p{
            padding-top: 2rem;
        }
    }
</style>