<template>
  <section id="resume" class="py-12 md:py-16 relative bg-slate-900/40">
    <div class="container mx-auto px-4 sm:px-6 lg:px-8 text-center">
      <motion.div
        :initial="{ opacity: 0, scale: 0.9 }"
        :whileInView="{ opacity: 1, scale: 1 }"
        :viewport="{ once: true }"
        :transition="{ duration: 0.6 }"
        class="max-w-3xl mx-auto"
      >
        <h2 class="text-2xl sm:text-3xl md:text-5xl font-orbitron mb-8 md:mb-10 neon-text-purple">
          Ready to Build the Future?
        </h2>

        <p class="text-slate-400 mb-8 md:mb-10 text-base sm:text-lg">
          Explore my experience, projects, and technical skills in frontend development.
        </p>

        <div class="flex flex-wrap justify-center gap-4 mb-10">
          <motion.span
            v-for="(item, index) in highlights"
            :key="index"
            :initial="{ opacity: 0, y: 10 }"
            :whileInView="{ opacity: 1, y: 0 }"
            :viewport="{ once: true }"
            :transition="{ duration: 0.4, delay: index * 0.1 }"
            class="text-xs md:text-sm font-mono text-blue-300 bg-blue-900/20 px-3 py-1 rounded-full border border-blue-500/20"
          >
            {{ item }}
          </motion.span>
        </div>

        <motion.a
          href="/resume/Venkateswarlu-Tiruveedula-Resume.pdf"
          target="_blank"
          rel="noopener noreferrer"
          :whileHover="{ scale: 1.05 }"
          :whileTap="{ scale: 0.95 }"
          class="inline-flex items-center gap-1 px-6 sm:px-10 py-3 sm:py-4 bg-purple-600/20 border border-purple-500 text-purple-300 font-orbitron rounded hover:bg-purple-600 hover:text-white transition-all duration-300 neon-box-purple"
          data-testid="btn-download-resume-section"
        >
          Resume <Icon icon="famicons:open-outline" class="h-4 w-4" />
        </motion.a>
      </motion.div>
    </div>
  </section>
</template>

<script setup>
import { motion } from "motion-v";

const highlights = [
  "4 Years Experience",
  "Vue.js & Nuxt.js",
  "React.js",
  "Resuable UI Development",
  "AI-Assisted Development",
];
</script>