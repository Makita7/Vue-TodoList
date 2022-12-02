<script setup>
    import '@fortawesome/free-solid-svg-icons';
    import BaseHeader from './components/BaseHeader.vue';
    import BaseInput from './components/BaseInput.vue';
import ListItems from './components/ListItems.vue';
</script>

<template>
    <div class="relative bottomBackground App">
        <div class="topBackground">
            <div class="absolute innerContainer">
                <BaseHeader/>
                <BaseInput/>
                <ListItems/>
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
    .dragtext{
        margin-top: 3rem;
        color: hsl(236deg 6% 52%);
        text-align: center;
    }
</style>
