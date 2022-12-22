
<script>
    export default{
        props:{ DarkMode: Boolean },
        methods: {
            ToggleDarkMode(){
                this.$emit('ToggleDarkMode')
            },
        }
    }
</script>


<template>
    <header>
        <h1>todo</h1>
        <button aria-label="toggle dark mode" v-show="!DarkMode" @click="ToggleDarkMode()">
            <fa class="iconW fa-2xl" icon="moon"/>
        </button>
        <button aria-label="toggle dark mode" v-show="DarkMode" @click="ToggleDarkMode()">
            <fa class="iconW fa-2xl" icon="sun"/>
        </button>
    </header>
</template>

<style scoped>
header{
    margin-top: 4rem;
    display: flex;
    text-align: center;
    justify-content: space-between;
}
    h1{
        text-transform: uppercase;
        color: white;
        text-shadow: rgb(24, 19, 37) 0px 4px 8px;
        font-size: 2.5rem;
        letter-spacing: 10px;
    }
    .iconW{
        color: rgba(232, 249, 255, 0.8);
        transition: 0.5s;
    }
    .iconW:hover{
        opacity: 1;
        color: white;
        scale: 1.1;
    }
    button{
        border-color: #ffffff00;
        background-color: #ffffff00;
    }
</style>