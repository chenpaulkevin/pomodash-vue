<script setup lang="ts">
import { RouterLink } from 'vue-router'
import { ref } from 'vue'
import Menu from '~icons/line-md/menu'
import MenuToClose from '~icons/line-md/menu-to-close-transition'
import gsap from 'gsap'


const isMenuOpen = ref(true)
const navLinks = ref([
    { name: 'Home', url: '/' },
    { name: 'About', url: '/about' },
    { name: 'Leaderboards', url: '/about' },
    { name: 'Get Started', url: '/about' },
])

function onBeforeEnter(el: any) {
    el.style.opacity = 0;
    el.style.transform = 'translateY(-100px)';
}

function onEnter(el: any, done: any) {
    gsap.to(el, {
        opacity: 1,
        transform: 'translateY(0px)',
        duration: 1,
        ease: 'expo.out',
        onComplete: done,
        delay: el.dataset.index * 0.2,
        immediateRender: false
    })
}

function onBeforeEnterHeader(el: any) {
    el.style.opacity = 0;
}

function onEnterHeader(el: any, done: any) {
    gsap.to(el, {
        opacity: 1,
        duration: 1,
        ease: 'expo.out',
        onComplete: done,
        delay: 0.4,
    })
}
</script>

<template>
    <nav class="sticky top-4 z-20 mb-4 bg-white">
        <div class="flex justify-between items-center rounded-lg  px-8 py-6 lg:px-16 md:py-8 border-black border-2 ">
            <RouterLink to="/">
                <div class="logo text-2xl md:text-4xl font-black font-display tracking-wider">Pomodash
                </div>
            </RouterLink>

            <div class="hidden md:block">
                <ul class="flex gap-4 items-center font-bold">
                    <li v-for="(link, index) in navLinks" :key="index" :data-index="index">
                        <RouterLink v-if="link.name === 'Get Started'" :to="link.url" class="button-primary font-black">{{
                            link.name }}</RouterLink>
                        <RouterLink v-else :to="link.url" class="nav-links">{{
                            link.name }}</RouterLink>
                    </li>
                </ul>
            </div>

            <div class="md:hidden justify-self-end">
                <div class="flex">
                    <Menu class="h-8 w-8 z-50 cursor-pointer" @click="isMenuOpen = !isMenuOpen" />
                </div>
            </div>
        </div>
    </nav>

    <Transition name="fade">
        <div v-if="isMenuOpen" class="fixed top-0 left-0 w-full h-screen origin-top bg-black z-40 p-10 md:hidden">
            <div class="flex h-full flex-col m-1 z-50">
                <TransitionGroup tag="div" class="flex justify-between" appear @before-enter="onBeforeEnterHeader"
                    @enter="onEnterHeader">
                    <RouterLink to="/" key="1">
                        <span @click="isMenuOpen = !isMenuOpen"
                            class="text-2xl text-white font-display font-black">Pomodash</span>
                    </RouterLink>
                    <MenuToClose key="2" @click="isMenuOpen = !isMenuOpen" class="h-8 w-8 z-50 text-white cursor-pointer" />
                </TransitionGroup>
                <div class="flex flex-col h-full justify-center items-center ">
                    <TransitionGroup appear @before-enter="onBeforeEnter" @enter="onEnter" tag="ul"
                        class="flex flex-col justify-center items-center gap-4">
                        <li v-for="(link, index) in navLinks" :key="index" :data-index="index">
                            <RouterLink @click="isMenuOpen = !isMenuOpen"
                                class="font-black font-display tracking-wider text-white text-4xl" :to="link.url">{{
                                    link.name }}</RouterLink>
                        </li>
                    </TransitionGroup>
                </div>
            </div>

        </div>
    </Transition>
</template>

<style scoped>
.fade-leave-to,
.fade-enter-from {
    transform: translateY(-100vh);
}

.fade-leave-from,
.fade-enter-to {
    transform: translateY(0);
}

.fade-leave-active,
.fade-enter-active {
    transition: .5s ease all;
}
</style>