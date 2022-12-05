<script>
    import '@fortawesome/free-solid-svg-icons';
    import BaseHeader from './components/BaseHeader.vue';
    import BaseInput from './components/BaseInput.vue';
    import BaseListFilters from './components/BaseListFilters.vue';
    import BaseListItem from './components/BaseListItem.vue';


    export default{
        components: {
            BaseHeader,
            BaseInput,
            BaseListFilters,
            BaseListItem,
        },
        data(){
            return{
                TodoList: [
                    { id: 1, task: 'Clean your room', done: false },
                    { id: 2, task: 'Go for a walk', done: true },
                    { id: 3, task: 'Do Homework', done: false },
                    { id: 4, task: 'Study Vue', done: false },
                ]
            }
        },
        methods: {
            DeleteAll(){
                this.TodoList = [];
            },
            DeleteItem(todo){
                this.TodoList = this.TodoList.filter((t) => t !== todo)
            },
            ToggleDone(todo){
                todo.done = !todo.done
            },
            ClearCompleted(){
                this.TodoList = this.TodoList.done.filter((t) => t === todo.done)
            }
        },
        computed: {
        }
    }
</script>

<template>
    <div class="relative bottomBackground App">
        <div class="topBackground">
            <div class="absolute innerContainer">
                <BaseHeader/>
                <BaseInput/>
                <div class="Wrapper">
                    <!-- <BaseListItem v-for="todo in TodoList" :key="todo.id" :task="todo.task" :done="todo.done" :id="todo.id" @DeleteItem="DeleteItem(todo)" @ToggleDone="ToggleDone()" /> -->


                    <div v-for="todo in TodoList" :key="todo.id">
                        <div class="flex TodoItem">
                            <div v-show="todo.done" class="checkWrapper">
                                <div class="check"  @click="ToggleDone(todo)" >
                                    <img alt="check" src="./assets/icon-check.svg"/>
                                </div>
                            </div>
                            <div v-show="!todo.done" class="checkWrapperFalse">
                                <div class="check"  @click="ToggleDone(todo)" >
                                    <img class="circle" alt="blanck done" src="./assets/white-circle.svg"/>
                                </div>
                            </div>
                            <p>{{todo.task}}</p>
                            <img @click="DeleteItem(todo)" src="./assets/icon-cross.svg" alt="delete todo item" class="delete"/>
                        </div>
                        <hr class="divider"/>
                    </div>


                    <BaseListFilters :TodoList="TodoList" @DeleteAll='DeleteAll()' />
                </div>
                <p class="dragtext">Drag and drop to reorder list</p>
            </div>
        </div>
    </div>
</template>

<style scoped>
    .topBackground{
        background-image: url('./assets/bg-desktop-light.jpg');
        background-repeat: no-repeat;
        background-size: cover;
        height: 18.5rem;
    }
    .innerContainer{
        width: 100vh;
        margin-left: 50vh;
    }
    .bottomBackground{
        background-color: hsl(0, 0%, 98%);
        height: 100vh;
    }
    .Wrapper{
        background-color: white;
        border-radius: 5px;
        width: 100%;
        padding: 15px 25px;
        box-sizing: border-box;
        box-shadow: 0px 0px 20px hsl(233deg 6% 71% / 64%);
    }
    .dragtext{
        margin-top: 3rem;
        color: hsl(236deg 6% 52%);
        text-align: center;
    }

    .checkWrapper{
        background: linear-gradient( 160deg ,hsl(192, 100%, 67%), hsl(280, 87%, 65%));
        height: 2rem;
        width: 2rem;
        border-radius: 50%;
        box-sizing: border-box;
    }
    .checkWrapperFalse{
        background: linear-gradient( 160deg ,hsl(233, 11%, 84%), hsl(233, 11%, 84%));
        height: 2rem;
        width: 2rem;
        border-radius: 50%;
        box-sizing: border-box;
        transition: all 2s ease-in-out;
    }
    .checkWrapperFalse:hover{
        background: linear-gradient( 160deg ,hsl(192, 100%, 67%), hsl(280, 87%, 65%));
    }
    .check{
        color: white;
    }
    .check img {
        margin: auto;
        padding-top: 0.6rem;
        display: block;
        width: 1rem;
    }
    .check .circle {
        margin: auto;
        padding-top: 0.15rem;
        display: block;
        width: 1.7rem;
    }
    img.delete {
        width: 1.3rem;
        height: 1.4rem;
        padding-top: 0.5rem;
    }
    .TodoItem p{
        padding: 0.5rem 1rem;
        width: 92%;
        box-sizing: border-box;
    }
    .divider{
        width: 107%;
        margin: 0.8rem 0;
        background-color: hsl(0, 0%, 98%);
        margin-left: -25px;
    }
</style>
