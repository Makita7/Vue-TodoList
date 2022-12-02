
<script setup>
import { ref } from 'vue';
import BaseListFilters from './BaseListFilters.vue';

    const Checkbox = ref(false);

</script>

<template>
    <div class="Wrapper">
        <div>
            <div class="flex TodoItem">
                <div v-show="Checkbox" class="checkWrapper">
                    <div class="check"  @click="(Checkbox = !Checkbox)" >
                        <img alt="check" src="../assets/icon-check.svg"/>
                    </div>
                </div>
                <div v-show="!Checkbox" class="checkWrapperFalse">
                    <div class="check"  @click="(Checkbox = !Checkbox)" >
                        <img class="circle" alt="blanck checkbox" src="../assets/white-circle.svg"/>
                    </div>
                </div>
                <p>task description in the todo list</p>
                <img src="../assets/icon-cross.svg" alt="delete todo item" class="delete">
            </div>
            <hr class="divider"/>
        </div>


        <div>
            <div class="flex TodoItem">
                <div v-show="Checkbox" class="checkWrapper">
                    <div class="check"  @click="(Checkbox = !Checkbox)" >
                        <img alt="check" src="../assets/icon-check.svg"/>
                    </div>
                </div>
                <div v-show="!Checkbox" class="checkWrapperFalse">
                    <div class="check"  @click="(Checkbox = !Checkbox)" >
                        <img class="circle" alt="blanck checkbox" src="../assets/white-circle.svg"/>
                    </div>
                </div>
                <p>task description in the todo list</p>
                <img src="../assets/icon-cross.svg" alt="delete todo item" class="delete">
            </div>
            <hr class="divider"/>
        </div>

        <BaseListFilters/>

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