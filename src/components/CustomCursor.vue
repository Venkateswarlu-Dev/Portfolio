<template>
  <motion.div
    class="hidden lg:block fixed top-0 left-0 w-4 h-4 bg-blue-500 rounded-full pointer-events-none z-[100] mix-blend-screen"
    :animate="{
      x: mousePosition.x - 8,
      y: mousePosition.y - 8,
    }"
    :transition="{ type: 'spring', stiffness: 500, damping: 28, mass: 0.5 }"
  />
  <motion.div
    class="hidden lg:block fixed top-0 left-0 w-12 h-12 border border-blue-500 rounded-full pointer-events-none z-[99]"
    :animate="{
      x: mousePosition.x - 24,
      y: mousePosition.y - 24,
    }"
    :transition="{ type: 'spring', stiffness: 150, damping: 20, mass: 0.8 }"
  />
</template>
<script setup>
import { ref, onMounted, onUnmounted } from "vue";
import { motion } from "motion-v";

const mousePosition = ref({
  x: 0,
  y: 0,
});

const updateMousePosition = (e) => {
  mousePosition.value = {
    x: e.clientX,
    y: e.clientY,
  };
};

onMounted(() => {
  window.addEventListener("mousemove", updateMousePosition);
});

onUnmounted(() => {
  window.removeEventListener("mousemove", updateMousePosition);
});
</script>
