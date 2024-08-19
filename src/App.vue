
<script setup>
    import {ref, defineAsyncComponent} from "vue"
	const current_screen = ref(defineAsyncComponent(() => import('./pages/login.vue')));
</script>

<template>
    <component :is="current_screen"></component>
</template>

<style scoped>
</style>
