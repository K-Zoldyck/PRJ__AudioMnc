
<script setup>
    import {ref,markRaw, onMounted } from "vue"
    import cmp_login from "./pages/login.vue"
    import cmp_sigin from "./pages/sigin.vue"
    import cmp_recov from "./pages/recov.vue"
    import cmp_mance from "./pages/mance.vue" // arquivo principal do app/site

    const TEMP_LOGGED_TOKEN = false // escreva true para ir direto para mance.vue
	const current_screen = ref({}) 
    
    onMounted(()=> {
        if ( TEMP_LOGGED_TOKEN ) {
            current_screen.value = markRaw(cmp_mance);
        }
    })

    current_screen.value = markRaw(cmp_login)

    const handle_events = (action) => {
        switch(action) {
            // login emmiters
                case "goto_sigin": current_screen.value = markRaw(cmp_sigin); break; // new account
                case "goto_recov": current_screen.value = markRaw(cmp_recov); break; // recovery password
                case "goto_mance": current_screen.value = markRaw(cmp_mance); break; // recovery password
        }
    }
</script>

<template>
    <component :is="current_screen" @action="handle_events"></component>
</template>

<style scoped>
</style>
