<template>
  <section id="experience" class="py-12 md:py-16 relative bg-slate-900/10">
    <div class="container mx-auto px-4 sm:px-6 lg:px-8">
      <motion.div
        :initial="{ opacity: 0, y: 30 }"
        :whileInView="{ opacity: 1, y: 0 }"
        :viewport="{ once: true }"
        :transition="{ duration: 0.6 }"
      >
        <h2
          class="text-2xl sm:text-3xl md:text-5xl font-orbitron mb-8 md:mb-10 flex items-center gap-4 justify-end"
        >
          <div class="h-px bg-slate-800 flex-grow mr-4"></div>
          Experience <span class="text-purple-500">.04</span>
        </h2>
      </motion.div>

      <div class="relative border-l border-purple-500/30 ml-2 sm:ml-4 md:ml-8">
        <motion.div
          v-for="(exp, index) in timeline"
          :key="index"
          :initial="{ opacity: 0, x: -30 }"
          :whileInView="{ opacity: 1, x: 0 }"
          :viewport="{ once: true }"
          :transition="{ duration: 0.5, delay: index * 0.2 }"
          class="mb-12 pl-8 relative"
        >
          <!-- Timeline Dot -->
          <div
            class="absolute w-4 h-4 bg-slate-950 border-2 border-purple-500 rounded-full -left-[9px] top-1 neon-box-purple"
          ></div>

          <div
            class="glass-card p-4 sm:p-6 rounded-lg hover:border-purple-500/50! hover:shadow-[0_0_20px_rgba(139,92,246,0.4)] transition-colors duration-300"
          >
            <div
              class="font-orbitron mb-2 flex flex-col sm:flex-row sm:items-baseline sm:justify-between gap-1 sm:gap-2"
            >
              <a :href="exp.link" target="_blank" class="text-lg sm:text-xl font-medium text-purple-500"
                >@{{ exp.company }}</a
              >
              <span class="text-slate-400 text-xs sm:text-md">{{ exp.period }}</span>
            </div>
            <!-- <span>{{ exp.period }}</span> -->

            <div
              v-for="role in exp.roles"
              :key="role.designation"
              class="relative border-l border-purple-500/30 ml-1 pl-4"
            >
              <span
                class="absolute -left-1.25 top-3 w-2 h-2 rounded-full bg-slate-950 border-2 border-purple-500 neon-box-purple"
              ></span>
              <!-- Role content -->
              <div class="mb-3">
                <div class="flex flex-wrap items-center gap-x-3 gap-y-1 mb-2 font-mono">
                  <h4 :class="['text-lg font-medium', exp.roles.length === 1 ? 'animate-pulse' : '']">
                    {{ role.designation }}
                  </h4>

                  <span v-if="role?.period" class="text-purple-400/40">|</span>

                  <span class="text-purple-500/90 text-sm">
                    {{ role.period }}
                  </span>
                </div>
                <p class="text-slate-400 text-md mb-2">
                  {{ role.desc }}
                </p>
                <div class="flex flex-wrap gap-2 mt-auto">
                  <span
                    v-for="t in role.techStack"
                    :key="t"
                    class="text-xs font-mono text-purple-400 bg-purple-900/20 px-2 py-1 rounded"
                  >
                    {{ t }}
                  </span>
                </div>
              </div>
            </div>

            <!-- <h3 class="text-xl font-orbitron mb-1 flex justify-between">
              <span class="text-white">{{ exp.role }}</span>
              <a :href="exp.link" target="_blank" class="text-blue-500">@{{ exp.company }}</a>
            </h3>
            <div class="text-purple-400 font-mono text-sm mb-4">{{ exp.period }}</div>
            <p class="text-slate-400">{{ exp.desc }}</p> -->
          </div>
        </motion.div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { motion } from "motion-v";

const timeline = [
  {
    company: "Bacancy Services",
    link: "https://www.bacancytechnology.com/",
    period: "SEP 2024 - MAR 2026 | Hyderabad",
    roles: [
      {
        designation: "Software Engineer",
        period: "",
        desc: "Built Vue.js 3, JavaScript, and TypeScript applications including a mobile e-commerce platform and video storytelling product, with reusable UI components, REST API integration, and frontend performance optimization.",
        techStack: [
          "Vue.js 3",
          "JavaScript",
          "Pinia",
          "TypeScript",
          "Bootstrap",
          "Tailwind CSS",
          "REST APIs",
          "Creatomate",
        ],
      },
    ],
  },
  {
    company: "Mantra Technologies",
    link: "https://mantragroup.com/",
    period: "APR 2022 - SEP 2024 | Hyderabad",
    roles: [
      {
        designation: "Software Developer",
        period: "JAN 2024 - SEP 2024",
        desc: "Developed configurable frontend plugins using Nuxt 3, Vue.js 3, TypeScript, and Tailwind CSS, and contributed to a No-Code App Builder for creating custom applications.",
        techStack: ["Nuxt 3", "Vue.js 3", "Pinia", "TypeScript", "Tailwind CSS"],
      },
      {
        designation: "Software Engineer-1",
        period: "OCT 2022 - DEC 2023",
        desc: "Worked on the CRM project and developed reusable frontend components using Vue.js and Nuxt.js, focusing on maintainable UI architecture, responsive interfaces, and scalable frontend features.",
        techStack: ["Vue.js", "Nuxt.js", "Pinia", "TypeScript", "Tailwind CSS"],
      },
      {
        designation: "Software Developer Trainee",
        period: "APR 2022 - SEP 2022",
        desc: "Worked on the CRM project, contributing to frontend development using Vue.js and JavaScript while gaining hands-on experience building and maintaining web application features.",
        techStack: ["Vue.js", "JavaScript", "Bootstrap Vue"],
      },
    ],
  },
  // {
  //   role: "Frontend Developer",
  //   projects: "No-Code App Builder",
  //   desc: "Implemented JSON-driven architecture and developed responsive interfaces.",
  // },
  // {
  //   role: "Frontend Developer",
  //   projects: "VR Property Showcase",
  //   desc: "Collaborated with teams to integrate APIs and improved UX in immersive web environments.",
  // },
  // {
  //   role: "Frontend Developer",
  //   projects: "AI Personalized Outreach Tools",
  //   desc: "Integrated AI APIs to deliver highly personalized experiences and workflows.",
  // },
];
</script>