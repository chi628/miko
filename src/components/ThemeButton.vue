<script setup>
import { computed, onMounted, ref } from "vue"
const isDarkMode = ref(false)
import DarkIcon from "../images/moon.png"
import LightIcon from "../images/sun.png"

const icon = computed(() => {
  return isDarkMode.value ? DarkIcon : LightIcon
})

onMounted(() => {
  if (window.matchMedia) {
    isDarkMode.value = window.matchMedia("(prefers-color-scheme: dark)").matches
  }
})
</script>
<template>
  <div class="w-10 h-10 rounded-full cursor-pointer" @click="isDarkMode = !isDarkMode">
    <img :src="icon.src" alt="" />
  </div>
</template>
