<template>
  <motion.div
    class="fixed top-0 left-0 right-0 h-1 bg-blue-500 origin-left z-50 neon-box-blue"
    :style="{ scaleX }"
  />
</template>
<script setup>
import { motion, useScroll, useSpring } from "motion-v";

const { scrollYProgress } = useScroll();

const scaleX = useSpring(scrollYProgress, {
  stiffness: 100,
  damping: 30,
  restDelta: 0.001,
});
</script>
