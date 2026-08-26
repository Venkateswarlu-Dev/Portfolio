<template>
  <motion.div
    class="fixed inset-0 z-[200] flex flex-col items-center justify-center bg-slate-950"
    :initial="{ opacity: 1 }"
    :exit="{ opacity: 0, y: -50 }"
    :transition="{ duration: 0.8, ease: 'easeInOut' }"
  >
    <div class="flex flex-col items-center">
      <motion.div
        :initial="{ opacity: 0, scale: 0.8 }"
        :animate="{ opacity: 1, scale: 1 }"
        :transition="{ duration: 0.5 }"
        class="text-4xl md:text-6xl font-orbitron font-bold text-white mb-8 neon-text-blue"
      >
        VT<span class="text-blue-500">.</span>
      </motion.div>

      <div class="w-64 h-1 bg-slate-800 rounded-full overflow-hidden relative">
        <motion.div
          class="absolute top-0 left-0 h-full bg-blue-500 neon-box-blue"
          :initial="{ width: '0%' }"
          :animate="{ width: `${Math.min(progress, 100)}%` }"
          :transition="{ ease: 'easeOut' }"
        />
      </div>

      <div class="mt-4 font-mono text-blue-400 text-sm">
        INITIALIZING SYSTEM... {{ Math.min(progress, 100) }}%
      </div>
    </div>
  </motion.div>
</template>
<script setup>
import { ref, defineEmits, onMounted, onUnmounted } from "vue";
import { motion } from "motion-v";

const emit = defineEmits(["complete"]);

const progress = ref(0);

let interval = null;

onMounted(() => {
  interval = setInterval(() => {
    progress.value += Math.floor(Math.random() * 15) + 5;

    if (progress.value >= 100) {
      progress.value = 100;

      clearInterval(interval);

      setTimeout(() => {
        emit("complete");
      }, 500);
    }
  }, 150);
});

onUnmounted(() => {
  clearInterval(interval);
});
</script>
