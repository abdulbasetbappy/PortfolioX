<template>
    <div :class="{ dark: isDarkMode }">
        <footer class="dark:text-slate-200 text-slate-800 text-center">
            <p class="2xs:text-xs lg:text-base">&copy; 2021 All Right Reserved By <strong>Abdul Baset Bappy</strong></p>
        </footer>
    </div>
</template>

<script setup lang="ts">
import { useDarkModeStore } from "~/store/darkMood";
const darkModeStore = useDarkModeStore();
const isDarkMode = computed(() => darkModeStore.darkMode);
</script>

<style scoped>

</style>