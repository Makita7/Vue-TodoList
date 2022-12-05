
<script>
    import BaseListFilters from './BaseListFilters.vue';
    import BaseListItem from './BaseListItem.vue';

    export default{
        name: 'ListItems',
        props: {TodoList:Object, DeleteAll:Event},
        components: {
            BaseListFilters,
            BaseListItem
        },
}
</script>

<template>
    <div class="Wrapper">
        <p>{{TodoList}}</p>
        <BaseListItem v-for="i in TodoList" :key="i.id" :task="i.task" :done="i.done" :id="i.id"/>
        <BaseListFilters :TodoList="TodoList" @DeleteAll="$emit('DeleteAll')"/>
    </div>
</template>

<style scoped>
    .Wrapper{
        background-color: white;
        border-radius: 5px;
        width: 100%;
        padding: 15px 25px;
        box-sizing: border-box;
        box-shadow: 0px 0px 20px hsl(233deg 6% 71% / 64%);
    }
</style>