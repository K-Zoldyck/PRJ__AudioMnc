
<script setup>
    import {ref,markRaw, onMounted } from "vue"
    import mod_a from "./mods/modA.vue"
    import mod_b from "./mods/modB.vue"
    import mod_c from "./mods/modC.vue"

    const current_screen = ref({}) 

    const changeTab = (tabId) =>{
        if (tabId == 1 ){ current_screen.value = markRaw(mod_a);}
        if (tabId == 2 ){ current_screen.value = markRaw(mod_b);}
        if (tabId == 3 ){ current_screen.value = markRaw(mod_c);}
    }

    current_screen.value = markRaw(mod_c)
</script>

<template>
    <main class="m-player">
        <h1>Sala Nome</h1>
        <nav class="tab-box">
            <div @click="changeTab(1)" class="tab"><img src="./icons/ic_001.svg" class="tab-icon">voice mode</div>
            <div @click="changeTab(2)" class="tab"><img src="./icons/ic_001.svg" class="tab-icon">interactive mode</div>
            <div @click="changeTab(3)" class="tab"><img src="./icons/ic_001.svg" class="tab-icon">manual mode</div>
        </nav>
    </main>
    <component :is="current_screen"></component>
</template>

<style scoped>
    .m-player {
        width: min(var(--min-w),var(--max-w));
        margin: 0 auto;
    }
    .m-player h1 {
        width: 100%;
        margin: 10px 0;
    }
    .tab-box {
        display: flex;
        gap: 15px;
        width: 100%;
        justify-content: center;
        align-self: center;
    }
        .tab {
            text-align: right;
            padding: 1% 3%;
        }
        .tab-icon {
            vertical-align: middle;
            margin-right: 5px;
        }
        .tab-selected {
            border: 1px solid rgb(75, 133, 75);
        }
</style>