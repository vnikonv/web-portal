<template>

    <header class = "z-[500] flex flex-row text-purple-300 font-bold w-screen items-center relative bg-gray-100 border-b-2 border-purple-400 max-sm:justify-between max-sm:relative p-2">
    <div class = "basis-1/4 items-center justify-start px-8 min-w-40 max-sm:basis-auto">
    <img src = "assets/images/favicon.ico" class = "w-10 h-10 bg-transparent">
    </div>
    <div class = "basis-1/4 max-sm:basis-auto"></div>

    <nav :class = "{'basis-1/2 flex flex-row items-center justify-end px-8 gap-4 max-sm:w-screen': !burger || burger,
    'max-sm:basis-auto max-sm:absolute max-sm:top-full max-sm:left-0 max-sm:justify-center max-sm:flex-col max-sm:gap-0 max-sm:bg-white max-sm:px-0': burger,
    'max-sm:hidden': !burger}">
    <NuxtLink to = "/" class = "my-auto p-2 max-sm:w-screen hover:bg-purple-300 hover:text-white max-sm:border-b-2 max-sm:border-purple-700 max-sm:text-center">Coordinates</NuxtLink>
    <div class = "my-auto p-2 max-sm:w-screen hover:bg-purple-300 hover:text-white max-sm:text-center max-sm:px-0 max-sm:pb-0" @click = "switch_submenu">Hydrology
        <div class = "absolute flex flex-col top-full bg-white text-purple-700 w-56 text-center max-sm:relative max-sm:w-full" v-show = "submenu">
            <NuxtLink to = "/Lab3" class = "my-auto p-2 border-0 bg-white hover:bg-purple-300 hover:text-white max-sm:w-full border-t-2 border-b-2
            border-t-purple-400 border-b-purple-700 max-sm:text-center">Water level</NuxtLink>
            <NuxtLink to = "/Lab4" class = "my-auto p-2 bg-white border-b-2 border-purple-700 hover:bg-purple-300 hover:text-white max-sm:w-full max-sm:text-center">Transparency</NuxtLink>
            <NuxtLink to = "/Lab5" class = "my-auto p-2 bg-white border-b-2 border-purple-700 hover:bg-purple-300 hover:text-white max-sm:w-full max-sm:text-center">Temperature</NuxtLink>
            <NuxtLink to = "/Lab6" class = "my-auto p-2 bg-white border-b-2 border-purple-700 hover:bg-purple-300 hover:text-white max-sm:w-full max-sm:text-center">Conductivity</NuxtLink>
        </div>
    </div>
        <NuxtLink to = "/inform" :class = "{'my-auto p-2 hover:bg-purple-300 hover:text-white max-sm:w-full max-sm:border-b-2 max-sm:border-purple-700 max-sm:text-center': submenu,
        'my-auto p-2 hover:bg-purple-300 hover:text-white max-sm:w-full max-sm:border-b-2 max-sm:border-t-2 max-sm:border-purple-700 max-sm:text-center': !submenu}">Pathogens</NuxtLink>
    </nav>

    <div v-if = "!burger" @click = "switch_burger" class = "max-sm:flex max-sm:flex-col max-sm:mr-8 max-sm:justify-between max-sm:items-center max-sm:w-8 max-sm:h-6">
        <span class = "h-[3px] w-full bg-blue-950"></span>
        <span class = "h-[3px] w-full bg-blue-950"></span>
        <span class = "h-[3px] w-full bg-blue-950"></span>
    </div>

    <div v-else class = "max-sm:flex max-sm:flex-col max-sm:mr-8 max-sm:justify-between max-sm:items-center max-sm:w-8 max-sm:h-6" @click = "switch_burger">
        <span class= "h-[3px] w-full bg-blue-950 rotate-45 relative top-[9px]"></span>
        <span class= "h-[3px] w-full bg-blue-950 opacity-0"></span>
        <span class="h-[3px] w-full bg-blue-950 relative bottom-3 rotate-[-45deg]"></span>
    </div>

    </header>

    <main class = "z-[2] flex h-screen p-0">
        <slot />
    </main>


    <footer class = "flex flex-row w-full bg-gray-100 border-t-2 border-purple-400 items-center justify-center px-4 py-2 gap-8">
        <a href="https://www.youtube.com/"><img src="assets/images/youtube.png" class="w-16 h-4 bg-transparent"></a>
        <a href="https://github.com/"><img src="assets/images/github.png" class="w-8 h-8 bg-transparent"></a>
        <a href="https://www.facebook.com/"><img src="assets/images/bsky.png "class = "w-8 h-8 bg-transparent"></a>
    </footer>

</template>

<script setup lang="ts">
import {ref} from 'vue'
const burger = ref<boolean> (false)
const submenu = ref<boolean> (false)
const switch_burger = ()=> {burger.value = !burger.value}
const switch_submenu = ()=> {submenu.value = !submenu.value}
</script>