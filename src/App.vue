<script setup>
    import '@fortawesome/free-solid-svg-icons';
    import BaseHeader from './components/BaseHeader.vue';
</script>

<template>
    <div class="relative bottomBackground App">
        <div class="topBackground">
            <div class="absolute">
                <BaseHeader/>
                <p>Drag and drop toreorder list</p>
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
    .bottomBackground{
        background-color: hsl(0, 0%, 98%);
        height: 100vh;
    }
</style>
