<script setup lang="ts">
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup
import { ref } from 'vue'
import Lottie from './components/Lottie.vue'
import ani01 from './assets/lottie-data/cash-or-card.json'

const animation = ref<HTMLElement>()
const defaultOptions = {
  animationData: ani01,
  loop: true,
  autoplay: true,
}

const handleAnimation = (anim: any) => {
  animation.value = anim
}
</script>

<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <lottie
    ref="animation"
    :options="defaultOptions"
    width="100%"
    height="100%"
    @animCreated="handleAnimation"
  />
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
