<script>
    import '@fortawesome/free-solid-svg-icons';
import { onMounted } from 'vue';
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
                ],
                All: [],
                Completed: [],
                Active: [],
                DarkMode: false,
                LastId: [],
                newTodo: '',
            }
        },
        methods: {
            ToggleDone(todo){
                todo.done = !todo.done
            },
            ToggleDarkMode(){
                this.DarkMode = !this.DarkMode
            },
            AddTodo(){
                if(this.newTodo.length > 0){
                    this.TodoList.push({
                        id: this.LastId,
                        task: this.newTodo,
                        done: false,
                    })
                    this.newTodo = ''
                }
            },
            DeleteAll(){
                this.TodoList = [];
                this.TodoList = []
                this.Completed = []
                this.Active = []
                this.All = []
            },
            DeleteItem(todo){
                this.TodoList = this.TodoList.filter((t) => t !== todo)
                this.Completed = this.Completed.filter((t) => t !== todo)
                this.Active = this.Active.filter((t) => t !== todo)
                this.All = this.All.filter((t) => t !== todo)
            },
            ClearCompleted(){
                this.Completed = this.Completed.filter((t) => t.done === false)
            },
            getAll(){
                return this.TodoList = this.All
            },
            getActive(){
                return this.TodoList = this.Active.filter((t) => t.done === false)
            },
            getCompleted(){
                return this.TodoList = this.Completed.filter((t) => t.done === true)
            }
        },
        mounted(){
            this.All = this.TodoList,
            this.Completed = this.TodoList,
            this.Active = this.TodoList
            this.LastId = this.TodoList.length
        },
        computed: {

        },
    }
</script>

<template>
    <div class="relative bottomBackground App">
        <div class="topBackground">
            <div class="absolute innerContainer">
                <BaseHeader :DarkMode="DarkMode" @ToggleDarkMode="ToggleDarkMode()"/>
                <input
                    type="text"
                    id="newTodo"
                    v-model="newTodo"
                    @keyup.enter="AddTodo()"
                />
                <div class="Wrapper">

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

                    <BaseListFilters :TodoList="TodoList" @getAll="getAll()" @DeleteAll='DeleteAll()' @getCompleted="getCompleted()" @getActive="getActive()"/>
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
        cursor: pointer;
    }
    .checkWrapperFalse{
        background: linear-gradient( 160deg ,hsl(233, 11%, 84%), hsl(233, 11%, 84%));
        height: 2rem;
        width: 2rem;
        border-radius: 50%;
        box-sizing: border-box;
        transition: all 2s ease-in-out;
        cursor: pointer;
    }
    .checkWrapperFalse:hover{
        background: linear-gradient( 160deg ,hsl(192, 100%, 67%), hsl(280, 87%, 65%));
    }
    .checkWrapper:hover{
        opacity: 0.8;
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
        cursor: pointer;
    }
    img.delete:hover {
        opacity: 0.5;
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
