<template>
  <section id="projects" class="py-24 relative">
    <div class="container mx-auto px-6">
      <motion.div
        :initial="{ opacity: 0, y: 30 }"
        :whileInView="{ opacity: 1, y: 0 }"
        :viewport="{ once: true }"
        :transition="{ duration: 0.6 }"
      >
        <h2 class="text-3xl md:text-5xl font-orbitron mb-16 flex items-center gap-4">
          <span class="text-blue-500">05.</span> Projects
          <div class="h-px bg-slate-800 flex-grow ml-4"></div>
        </h2>
      </motion.div>

      <div class="grid md:grid-cols-2 gap-8">
        <motion.div
          v-for="(project, index) in projects"
          :key="index"
          :initial="{ opacity: 0, y: 50 }"
          :whileInView="{ opacity: 1, y: 0 }"
          :viewport="{ once: true }"
          :transition="{ duration: 0.5, delay: index * 0.1 }"
          :whileHover="{ y: -10 }"
          class="glass-card rounded-xl group group/title relative overflow-hidden"
        >
          <video
            :src="project.video"
            autoplay
            muted
            loop
            playsinline
            class="w-full h-auto object-contain rounded-lg transition-transform duration-500 group-hover:scale-[1.02]"
          ></video>
          <div
            class="absolute inset-0 bg-gradient-to-br from-blue-500/10 to-purple-600/10 opacity-0 group-hover:opacity-100 transition-opacity duration-500"
          ></div>

          <div class="relative p-6 z-10">
            <a
              :href="project.link"
              target="_blank"
              rel="noopener noreferrer"
              class="inline-flex items-center gap-1 mb-4"
            >
              <h3 class="text-2xl font-orbitron transition-colors group-hover/title:text-blue-400">
                {{ project.title }}
              </h3>
              <Icon
                icon="famicons:open-outline"
                class="w-4 h-4 text-blue-400 opacity-0 transition-opacity group-hover/title:opacity-100"
              />
            </a>
            <p class="text-slate-400 mb-4">{{ project.description }}</p>
            <div class="flex flex-wrap gap-2 mt-auto">
              <span
                v-for="t in project.tech"
                :key="t"
                class="text-xs font-mono text-blue-400 bg-blue-900/20 px-2 py-1 rounded"
              >
                {{ t }}
              </span>
            </div>
          </div>
        </motion.div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { motion } from "motion-v";

const projects = [
  {
    title: "DevToolKit",
    link: "https://dev-tool-kit-app.vercel.app/",
    video: "/videos/devtoolkit.mp4",
    description:
      "Developer productivity toolkit for working with APIs, JSON, data formats, and developer utilities.",
    tech: ["Vue.js", "Nuxt.js", "JavaScript", "TypeScript", "Tailwind CSS"],
  },
  // {
  //   title: "No-Code App Builder",
  //   description:
  //     "JSON-driven dynamic UI platform enabling users to construct applications visually.",
  //   tech: ["Vue.js", "TypeScript", "Tailwind CSS"],
  // },
  // {
  //   title: "VR Property Showcase",
  //   description:
  //     "Immersive real estate VR platform bringing properties to life directly in the browser.",
  //   tech: ["Unity", "WebXR", "VR"],
  // },
  // {
  //   title: "AI Outreach Tool",
  //   description: "AI-powered personalized email and LinkedIn outreach automation.",
  //   tech: ["Vue.js", "AI APIs"],
  // },
];
</script>
