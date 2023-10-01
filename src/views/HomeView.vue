<script setup lang="ts">
import { RouterLink } from 'vue-router'
</script>

<template>
  <main>
    <div class="flex flex-wrap lg:flex-nowrap p-6 gap-5 h-min-screen">
      <div class="w-full h-auto self-center content-center justify-center p-4">
        <h1 class="text-4xl lg:text-6xl tracking-wider font-display font-black mb-4">Track Your Productivity Mileage
        </h1>
        <h3 class="text-xl lg:text-2xl tracking-wide mb-6">Join the league of top performers in the global productivity
          marathon and leave your mark on the leaderboard.
        </h3>
        <div
          class="button-group flex flex-col items-start space-y-3 sm:space-x-4 sm:space-y-0 sm:items-center sm:flex-row">
          <RouterLink
            class="button-primary w-full md:w-auto px-4 py-2 align-end md:px-6 md:py-2 font-black text-lg rounded-md border border-2 border-primary cursor-pointer ease-in-out duration-300 hover:-translate-y-1"
            to="/"> Get Started</RouterLink>
          <RouterLink
            class="button-primary w-full md:w-auto px-4 py-2 align-end md:px-6 md:py-2 font-black text-lg rounded-md border border-2 border-primary cursor-pointer ease-in-out duration-300 hover:-translate-y-1"
            to="/"> Learn More</RouterLink>
        </div>

      </div>
      <div class="w-full h-5/6 order-first lg:order-last"><img src="/Hard.png" alt="" srcset="">
      </div>
    </div>
  </main>
</template>
