
<script>
    export default{
        name: 'ListFilters',
        props: ['TodoList'],
        methods: {
            DeleteAll(){
                this.TodoList = []
            }
        }
    }

</script>

<template>
    <div class="flex">
        <div class="col count">
            5 items left
        </div>
        <div class="col flex filters">
            <p>All</p>
            <p>Active</p>
            <p>Completed</p>
        </div>
        <div class="col">
            <button>
                Clear Completed
            </button>
            <button @click="DeleteAll">
                Clear All
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