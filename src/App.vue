<template>
  <div
    class="bg-[#020617] min-h-screen text-slate-200 selection:bg-blue-500/30 selection:text-blue-200 font-sans overflow-x-hidden"
  >
    <AnimatePresence>
      <LoadingScreen v-if="isLoading" @complete="handleComplete"
    /></AnimatePresence>

    <CustomCursor />
    <ScrollProgress />

    <!-- Floating Particles Background CSS -->
    <div class="fixed inset-0 z-0 pointer-events-none overflow-hidden">
      <div
        v-for="(particle, index) in particles"
        :key="index"
        class="absolute rounded-full bg-blue-500/20 blur-[2px]"
        :style="{
          width: particle.size + 'px',
          height: particle.size + 'px',
          top: particle.top + '%',
          left: particle.left + '%',
          animation: `float ${particle.duration}s linear infinite`,
          animationDelay: `-${particle.delay}s`,
        }"
      />
    </div>
    <nav class="glass-card fixed w-full z-50 border-b-0 py-4 backdrop-blur-md">
      <div class="container mx-auto px-6 flex justify-between items-center">
        <div class="text-white font-orbitron font-bold tracking-widest text-xl neon-text-blue">
          VT<span class="text-blue-500">.</span>
        </div>
        <div class="hidden md:flex gap-8 font-orbitron text-sm">
          <a
            v-for="nav in navLinks"
            :key="nav.router"
            :href="nav.router"
            :class="`hover:text-${nav.color}-400 transition-colors`"
            >{{ nav.name }}</a
          >
        </div>
      </div>
    </nav>
    <main class="relative z-10">
      <Hero v-if="!isLoading" />
      <About />
      <Skills />
      <Tools />
      <Experience />
      <Projects />
      <Resume />
      <Contact />
    </main>

    <div class="relative z-10">
      <Footer />
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";
import LoadingScreen from "@/components/LoadingScreen.vue";
import CustomCursor from "@/components/CustomCursor.vue";
import ScrollProgress from "@/components/ScrollProgress.vue";
import Hero from "@/components/Hero.vue";
import About from "@/components/About.vue";
import Skills from "@/components/Skills.vue";
import Tools from "@/components/Tools.vue";
import Experience from "@/components/Experience.vue";
import Projects from "@/components/Projects.vue";
import Resume from "@/components/Resume.vue";
import Contact from "@/components/Contact.vue";
import Footer from "@/components/Footer.vue";

const isLoading = ref(true);

const handleComplete = () => {
  isLoading.value = false;
};

const particles = Array.from({ length: 20 }, () => ({
  size: Math.random() * 6 + 2,
  top: Math.random() * 100,
  left: Math.random() * 100,
  duration: Math.random() * 10 + 10,
  delay: Math.random() * 10,
}));

const navLinks = [
  { name: "About", router: "#about", color: "blue" },
  { name: "Skills", router: "#skills", color: "purple" },
  { name: "Tools", router: "#tools", color: "blue" },
  { name: "Experience", router: "#experience", color: "purple" },
  {
    name: "Projects",
    router: "#projects",
    color: "blue",
  },
  {
    name: "Resume",
    router: "#resume",
    color: "purple",
  },
  {
    name: "Contact",
    router: "#contact",
    color: "blue",
  },
];
</script>

<style>
@keyframes float {
  0% {
    transform: translateY(0) translateX(0);
    opacity: 0;
  }

  50% {
    opacity: 1;
  }

  100% {
    transform: translateY(-100vh) translateX(50px);
    opacity: 0;
  }
}
</style>
