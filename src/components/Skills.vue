<template>
  <section id="skills" class="py-24 relative bg-slate-900/30">
    <div class="container mx-auto px-6">
      <motion.div
        :initial="{ opacity: 0, y: 30 }"
        :whileInView="{ opacity: 1, y: 0 }"
        :viewport="{ once: true }"
        :transition="{ duration: 0.6 }"
      >
        <h2 class="text-3xl md:text-5xl font-orbitron mb-16 flex items-center gap-4 justify-end">
          <div class="h-px bg-slate-800 flex-grow mr-4"></div>
          Skills <span class="text-purple-500">.02</span>
        </h2>
      </motion.div>

      <div class="flex flex-wrap justify-center gap-6">
        <motion.div
          v-for="skill in skills"
          :key="skill"
          :initial="{ opacity: 0, scale: 0.8 }"
          :whileInView="{ opacity: 1, scale: 1 }"
          :viewport="{ once: true }"
          :transition="{ duration: 0.4, delay: index * 0.05 }"
          :whileHover="{
            scale: 1.1,
            boxShadow: '0 0 20px rgba(139, 92, 246, 0.4)',
            borderColor: 'rgba(139, 92, 246, 0.8)',
          }"
          class="glass-card px-6 py-3 rounded-full border border-slate-700 text-slate-300 font-orbitron text-sm md:text-base cursor-pointer"
        >
          {{ skill }}
        </motion.div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { motion } from "motion-v";

const skills = [
  "Vue.js",
  "Nuxt.js",
  "React.js",
  "JavaScript",
  "TypeScript",
  "Tailwind CSS",
  "Pinia",
  "HTML/CSS",
  "Bootstrap",
  "REST APIs",
  "Git",
  "GitHub",
  "Postman",
];
</script>
