<script>
    import '@fortawesome/free-solid-svg-icons';
    import BaseHeader from './components/BaseHeader.vue';
    import BaseListFilters from './components/BaseListFilters.vue';

    export default{
        components: {
            BaseHeader,
            BaseListFilters,
        },
        data(){
            return{
                TodoList: [],
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
                localStorage.setItem('LocalTodoList', JSON.stringify(this.TodoList))
            },
            ToggleDarkMode(){
                this.DarkMode = !this.DarkMode
                localStorage.setItem('LocalDarkMode', JSON.stringify(this.DarkMode));
                console.log(this.DarkMode)
            },
            AddTodo(){
                if(this.newTodo.length > 0){
                    this.TodoList.push({
                        id: this.LastId,
                        task: this.newTodo,
                        done: false,
                    })
                    this.newTodo = ''
                    this.All = this.TodoList
                    localStorage.setItem('LocalTodoList', JSON.stringify(this.TodoList))
                }
            },
            DeleteAll(){
                this.TodoList = []
                this.Completed = []
                this.Active = []
                this.All = []
                localStorage.setItem('LocalTodoList', JSON.stringify(this.TodoList))
            },
            DeleteItem(todo){
                this.TodoList = this.TodoList.filter((t) => t !== todo)
                this.Completed = this.Completed.filter((t) => t !== todo)
                this.Active = this.Active.filter((t) => t !== todo)
                this.All = this.All.filter((t) => t !== todo)
                localStorage.setItem('LocalTodoList', JSON.stringify(this.TodoList))
            },
            ClearCompleted(){
                this.TodoList = this.TodoList.filter((t) => t.done === false)
                this.All = this.All.filter((t) => t.done === false)
            },
            getAll(){
                return this.TodoList = this.All
            },
            getActive(){
                return this.TodoList = this.All.filter((t) => t.done === false)
            },
            getCompleted(){
                return this.TodoList = this.All.filter((t) => t.done === true)
            }
        },
        setup(){
        },
        created(){
            let DataTodoList = localStorage.getItem('LocalTodoList');
            if(DataTodoList != null){
                this.TodoList = JSON.parse(DataTodoList);
            }
            let DataDarkMode = localStorage.getItem('LocalDarkMode');
            if(DataDarkMode != null){
                this.DarkMode = JSON.parse(DataDarkMode);
            }
        },
        mounted(){
            this.All = this.TodoList
        },
        watch() {
        },
    }
</script>

<template>
    <div class="relative App bodyLight" :class="{ bodyDark: DarkMode }" >
        <div class="topBackground" :class="{ topBackgroundDark: DarkMode }">
            <div class="absolute innerContainer">
                <BaseHeader :DarkMode="DarkMode" @ToggleDarkMode="ToggleDarkMode()"/>
                <input
                    type="text"
                    id="newTodo"
                    v-model="newTodo"
                    @keyup.enter="AddTodo()"
                    :class="{ inputDark: DarkMode }"
                />
                <div class="Wrapper" :class="{ WrapperDark: DarkMode }">
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
                            <p class="pointer">{{todo.task}}</p>
                            <img @click="DeleteItem(todo)" src="./assets/icon-cross.svg" alt="delete todo item" class="delete"/>
                        </div>
                        <hr class="divider" :class="{ dividerDark:DarkMode }" />
                    </div>
                    <BaseListFilters :All="All" @getAll="getAll()" @DeleteAll='DeleteAll()' @getCompleted="getCompleted()" @getActive="getActive()" @ClearCompleted="ClearCompleted()" :DarkMode="DarkMode"/>
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
        transition: 1s ease-in-out;
    }
    .topBackgroundDark{
        background-image: url('./assets/bg-desktop-dark.jpg') !important;
        transition: 1s ease-in-out;
    }
    .innerContainer{
        width: 100vh;
        margin-left: 50vh;
    }
    .bodyLight{
        background-color: hsl(0, 0%, 98%);
        min-height: 200vh;
        transition: 1s ease-in-out;
    }
    .bodyDark{
        background-color: hsl(235, 21%, 11%) !important;
    }
    .Wrapper{
        background-color: white;
        border-radius: 5px;
        width: 100%;
        padding: 15px 25px;
        box-sizing: border-box;
        box-shadow: 0px 0px 20px hsl(233deg 6% 71% / 64%);
    }
    .WrapperDark{
        background-color: hsl(235, 24%, 19%);
        color: hsl(234, 39%, 85%);
        box-shadow: 0px 0px 20px hsl(0, 0%, 0%);
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
    input:focus-visible {
        outline: hsla(234, 39%, 85%, 0);
        border-color: rgba(250, 235, 215, 0);
    }
    .inputDark{
        background-color: hsl(235, 24%, 19%);
        color: hsl(0, 0%, 100%);
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
        border-bottom-color: hsl(0, 0%, 98%);
        border-width: 1px;
        transition: 0.5s ease-in-out;
    }
    .dividerDark{
        background-color: hsl(233, 14%, 35%);
        border-bottom-color: hsl(233, 14%, 35%);
    }
    .dragtext{
            margin-bottom: 3rem;
        }
    .pointer{
        cursor: pointer;
    }
    @media (min-width: 1920px){
        .divider{
            width: 105.5%;
        }
        .check .circle{
            padding-left: 0.07rem;
        }
    }
    @media only screen and (min-width: 768px) and (max-width: 1300px) and (orientation:landscape){
        .innerContainer {
            width: 75%;
            margin-left: 12.5%;
        }
        .divider{
            width: 105.5%;
        }
    }
    @media only screen and (min-width: 768px) and (max-width: 1300px) and (orientation:portrait){
        .innerContainer {
            width: 80%;
            margin-left: 10%;
        }
        .divider{
            width: 108%;
        }
    }
    @media (max-width: 767px){
        .innerContainer {
            width: 90%;
            margin-left: 5%;
        }
        .divider{
            width: 117%;
        }
        .checkWrapperFalse{
            width: 2.2rem;
        }
        .checkWrapper{
            width: 2.2rem;
        }
        .bodyLight{
            background-color: hsl(0, 0%, 98%);
            min-height: 400vh;
        }
    }
    @media (max-width: 767px) and (orientation:landscape){
        .divider {
            width: 107.5%;
        }
        .bodyLight{
            background-color: hsl(0, 0%, 98%);
            min-height: 400vh;
        }
    }
</style>
