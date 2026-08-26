<template>
  <section id="hero" class="relative min-h-screen flex items-center justify-center overflow-hidden">
    <CyberBackground />
    <div
      class="relative z-10 container mx-auto px-6 flex flex-col lg:flex-row items-center justify-between gap-12"
    >
      <!-- Left content -->
      <div class="flex-1 max-w-2xl">
        <motion.div
          :initial="{ opacity: 0, x: -40 }"
          :animate="{ opacity: 1, x: 0 }"
          :transition="{ duration: 0.7, delay: 0.2 }"
        >
          <div class="flex items-center gap-3 mb-6">
            <div
              class="w-2 h-2 rounded-full bg-blue-500 shadow-[0_0_8px_rgba(59,130,246,1)] animate-pulse"
            />
            <span class="text-blue-400 font-orbitron tracking-[0.25em] text-xs uppercase"
              >System Online // Welcome</span
            >
          </div>

          <h1 class="text-5xl md:text-7xl font-bold font-orbitron text-white mb-4 leading-tight">
            Venkateswarlu<br />
            <span
              class="text-transparent bg-clip-text bg-gradient-to-r from-blue-400 via-purple-400 to-blue-600"
            >
              Tiruveedula
            </span>
          </h1>

          <div class="h-px w-32 bg-gradient-to-r from-blue-500 to-purple-500 mb-6" />
          <div class="typing-line glass-card rounded-full border border-slate-700" data-reveal>
            <span>Building as a</span>
            <RoleTypewriter />
          </div>

          <p
            class="text-lg md:text-xl text-slate-300 font-light mb-3 border-l-2 border-purple-500 pl-4"
          >
            Frontend Developer | React.js | Vue.js | Nuxt.js | AI Enthusiast
          </p>
          <p class="text-slate-400 mb-10 text-base max-w-xl leading-relaxed">
            Frontend developer passionate about building scalable, user-friendly web applications
            with clean UI, high performance, and real-world impact.
          </p>

          <div class="flex flex-wrap gap-4 mb-12">
            <motion.a
              href="#projects"
              :whileHover="{ scale: 1.05 }"
              :whileTap="{ scale: 0.97 }"
              class="px-7 py-3 bg-blue-600/10 border border-blue-500/70 text-blue-400 font-orbitron text-sm rounded hover:bg-blue-600 hover:text-white hover:border-blue-600 hover:shadow-[0_0_20px_rgba(59,130,246,0.4)] transition-all duration-300"
              data-testid="btn-view-projects"
            >
              View Projects
            </motion.a>
            <motion.a
              href="#resume"
              :whileHover="{ scale: 1.05 }"
              :whileTap="{ scale: 0.97 }"
              class="px-7 py-3 bg-purple-600/10 border border-purple-500/70 text-purple-400 font-orbitron text-sm rounded hover:bg-purple-600 hover:text-white hover:border-purple-600 hover:shadow-[0_0_20px_rgba(139,92,246,0.4)] transition-all duration-300"
              data-testid="btn-download-resume"
            >
              Download Resume
            </motion.a>
            <motion.a
              href="#contact"
              :whileHover="{ scale: 1.05 }"
              :whileTap="{ scale: 0.97 }"
              class="px-7 py-3 bg-white/5 border border-slate-600 text-slate-300 font-orbitron text-sm rounded hover:bg-white/10 hover:border-slate-400 transition-all duration-300"
              data-testid="btn-contact-me"
            >
              Contact Me
            </motion.a>
          </div>
        </motion.div>
      </div>

      <!-- Right: Atom hand animation -->
      <AtomHandAnimation />

      <!-- <motion.img
        src="/cyber-hand.png"
        alt="Cyber Hand"
        class="w-full max-w-sm lg:max-w-2xl"
        :initial="{ opacity: 0, x: 40 }"
        :animate="{ opacity: 1, x: 0 }"
        :transition="{ duration: 0.7, delay: 0.4 }"
      /> -->
      <!-- <motion.div
        :initial="{ opacity: 0, x: 40 }"
        :animate="{ opacity: 1, x: 0 }"
        :transition="{ duration: 0.7, delay: 0.5 }"
        class="flex-shrink-0 grid grid-cols-2 gap-4"
      >
        <motion.div
          v-for="stat in statsData"
          :key="stat.label"
          :initial="{ opacity: 0, y: 20 }"
          :animate="{ opacity: 1, y: 0 }"
          :transition="{ delay: 0.6 + i * 0.1 }"
          :whileHover="{ scale: 1.05, borderColor: 'rgba(139,92,246,0.6)' }"
          class="bg-white/5 backdrop-blur-md border border-white/10 rounded-xl p-5 text-center min-w-[120px] hover:shadow-[0_0_20px_rgba(59,130,246,0.15)] transition-all duration-300"
        >
          <div
            class="text-3xl font-bold font-orbitron text-transparent bg-clip-text bg-gradient-to-br from-blue-400 to-purple-500 mb-1"
          >
            {{ stat.value }}
          </div>
          <div class="text-slate-400 text-xs font-orbitron tracking-widest uppercase">
            {{ stat.label }}
          </div>
        </motion.div>
      </motion.div> -->
    </div>

    <!-- Scroll indicator -->
    <motion.div
      class="absolute bottom-8 left-1/2 -translate-x-1/2 flex flex-col items-center gap-2 text-slate-500"
      :animate="{ y: [0, 8, 0] }"
      :transition="{ repeat: Infinity, duration: 2, ease: 'easeInOut' }"
    >
      <span class="text-xs font-orbitron tracking-widest uppercase">Scroll</span>
      <div class="bg-gradient-to-b w-px h-10 from-blue-500/60 to-transparent" />
    </motion.div>
  </section>
</template>

<script setup>
import CyberBackground from "./CyberBackground.vue";
import RoleTypewriter from "./RoleTypewriter.vue";
import AtomHandAnimation from "./AtomHandAnimation.vue";
import { motion } from "motion-v";

// const statsData = [
//   { label: "Years Exp", value: "4" },
//   { label: "Projects Delivered", value: "7+" },
//   { label: "Tech Stack", value: "Vue.js + React.js" },
//   { label: "Domains", value: "AI & Web Apps" },
// ];
</script>
