
<script setup>

</script>


<template>
    <header>
        <h1>todo</h1>
        <fa class="iconW fa-2xl" icon="moon"/>
        <!-- <fa class="iconW" icon="sun"/> -->
    </header>
</template>

<style scoped>
header{
    margin-top: 4rem;
    width: 100vh;
    display: flex;
    margin-left: 50vh;
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
</style>