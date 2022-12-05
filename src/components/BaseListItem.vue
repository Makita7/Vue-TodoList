
<script>
    export default{
        name: 'TodoList',
        props: {
            id: Number,
            task: String,
            done: Boolean
        },
        methods: {
            DeleteItem(){
                this.$emit('DeleteItem')
            },
            ToggleDone(){
                this.$emit('ToogleDone')
            }
        }
    }

</script>

<template>
    <div>
        <div class="flex TodoItem">
            <div v-show="done" class="checkWrapper">
                <div class="check"  @click="ToggleDone(todo)" >
                    <img alt="check" src="../assets/icon-check.svg"/>
                </div>
            </div>
            <div v-show="!done" class="checkWrapperFalse">
                <div class="check"  @click="ToggleDone(todo)" >
                    <img class="circle" alt="blanck done" src="../assets/white-circle.svg"/>
                </div>
            </div>
            <p>{{task}}</p>
            <img @click="DeleteItem(todo)" src="../assets/icon-cross.svg" alt="delete todo item" class="delete"/>
        </div>
        <hr class="divider"/>
    </div>
</template>

<style scoped>
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