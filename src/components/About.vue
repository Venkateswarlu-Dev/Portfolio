<template>
  <section id="about" class="py-24 relative">
    <div class="container mx-auto px-6">
      <motion.div
        :initial="{ opacity: 0, y: 30 }"
        :whileInView="{ opacity: 1, y: 0 }"
        :viewport="{ once: true }"
        :transition="{ duration: 0.6 }"
      >
        <h2 class="text-3xl md:text-5xl font-orbitron mb-12 flex items-center gap-4">
          <span class="text-blue-500">01.</span> About
          <div class="h-px bg-slate-800 flex-grow ml-4"></div>
        </h2>
      </motion.div>

      <div class="grid md:grid-cols-2 gap-12 items-center">
        <motion.div
          :initial="{ opacity: 0, x: -30 }"
          :whileInView="{ opacity: 1, x: 0 }"
          :viewport="{ once: true }"
          :transition="{ duration: 0.6, delay: 0.2 }"
          class="text-slate-300 leading-relaxed text-lg"
        >
          <p class="mb-6">
            Frontend Developer with 4 years of experience building scalable web applications using
            React.js, Vue.js, Nuxt.js, JavaScript, TypeScript, and Tailwind CSS. I specialize in
            creating reusable component architectures, responsive user interfaces, and
            performance-optimized applications that deliver excellent user experiences.
          </p>
          <p>
            Throughout my career, I have worked on CRM platforms, Plugins, No-Code App Builders,
            AI-powered tools,and video storytelling platforms. I enjoy solving complex frontend
            challenges, collaborating with cross-functional teams, and transforming business
            requirements into intuitive, high-quality products.
          </p>
        </motion.div>

        <motion.div
          :initial="{ opacity: 0, x: 30 }"
          :whileInView="{ opacity: 1, x: 0 }"
          :viewport="{ once: true }"
          :transition="{ duration: 0.6, delay: 0.4 }"
          class="grid grid-cols-2 gap-6"
        >
          <motion.div
            v-for="(stat, index) in statsData"
            :key="index"
            class="glass-card p-6 rounded-lg border-0! border-l-2! border-blue-500! hover:border-purple-500! transition-all duration-300"
          >
            <div class="text-blue-400 font-orbitron text-2xl font-bold mb-2">
              {{ stat.value }}
            </div>
            <div class="text-slate-400 text-sm">{{ stat.label }}</div>
          </motion.div>
        </motion.div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { motion, translateAxis } from "motion-v";

const statsData = [
  { label: "Experience", value: "4 Years" },
  { label: "Production Projects", value: "7+" },
  { label: "Core Stack", value: "React.js + Vue.js" },
  { label: "Focus", value: "AI & Web Apps" },
];
</script>
