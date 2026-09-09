<template>
  <section id="tools" class="py-12 md:py-16 relative bg-slate-900/20">
    <div class="container mx-auto px-4 sm:px-6 lg:px-8">
      <motion.div
        :initial="{ opacity: 0, y: 30 }"
        :whileInView="{ opacity: 1, y: 0 }"
        :viewport="{ once: true }"
        :transition="{ duration: 0.6 }"
      >
        <h2 class="text-2xl sm:text-3xl md:text-5xl font-orbitron mb-8 md:mb-10 flex items-center gap-4">
          <span class="text-blue-500">03.</span> Tools
          <div class="h-px bg-slate-800 flex-grow ml-4"></div>
        </h2>
        <p
          class="max-w-2xl mr-auto text-left text-slate-400 leading-relaxed mb-8 md:mb-10 text-sm sm:text-base"
        >
          A focused toolkit for building thoughtful interfaces, exploring new ideas, and bringing
          ambitious products to life.
        </p>
      </motion.div>

      <div class="grid lg:grid-cols-2 gap-6 md:gap-8">
        <motion.article
          v-for="(group, index) in toolGroups"
          :key="group.label"
          :initial="{ opacity: 0, y: 40 }"
          :whileInView="{ opacity: 1, y: 0 }"
          :viewport="{ once: true }"
          :transition="{ duration: 0.6, delay: index * 0.15 }"
          :class="[
            'glass-card rounded-2xl p-6 md:p-8 border-t-2!',
            group.accent === 'purple' ? 'border-t-purple-500/70!' : 'border-t-blue-500/70!',
          ]"
        >
          <div class="flex items-start justify-between gap-6 mb-8">
            <div>
              <p
                :class="[
                  'font-mono text-xs tracking-[0.24em] mb-3',
                  group.accent === 'purple' ? 'text-purple-400' : 'text-blue-400',
                ]"
              >
                {{ group.eyebrow }}
              </p>
              <h3 class="text-2xl md:text-3xl font-orbitron text-white flex items-center gap-2">
                <Icon
                  :icon="group.icon"
                  :ssr="true"
                  :class="[
                    'h-5 w-5',
                    group.accent === 'purple' ? 'text-purple-400' : 'text-blue-500',
                  ]"
                />
                {{ group.label }}
              </h3>
            </div>
            <span
              :class="[
                'shrink-0 w-11 h-11 rounded-full border flex items-center justify-center font-orbitron text-sm',
                group.accent === 'purple'
                  ? 'border-purple-500/40 text-purple-300 bg-purple-500/10'
                  : 'border-blue-500/40 text-blue-300 bg-blue-500/10',
              ]"
            >
              {{ String(index + 1).padStart(2, "0") }}
            </span>
          </div>

          <p class="text-slate-400 leading-relaxed mb-8 max-w-md">{{ group.description }}</p>

          <div class="grid sm:grid-cols-2 gap-3">
            <motion.div
              v-for="(tool, toolIndex) in group.tools"
              :key="tool.name"
              :initial="{ opacity: 0, x: -12 }"
              :whileInView="{ opacity: 1, x: 0 }"
              :viewport="{ once: true }"
              :transition="{ duration: 0.35, delay: index * 0.15 + toolIndex * 0.06 }"
              :whileHover="{ x: 4 }"
              :class="[
                'group/tool flex items-center gap-3 rounded-lg border bg-slate-950/40 px-4 py-3 transition-colors',
                group.accent === 'purple'
                  ? 'border-purple-500/15 hover:border-purple-500/50'
                  : 'border-blue-500/15 hover:border-blue-500/50',
              ]"
            >
              <span
                :class="[
                  'w-2 h-2 rounded-full transition-transform group-hover/tool:scale-150',
                  group.accent === 'purple' ? 'bg-purple-400' : 'bg-blue-400',
                ]"
              />
              <span>
                <span class="block text-sm text-slate-200">{{ tool.name }}</span>
                <span class="block text-xs text-slate-500 font-mono mt-0.5">{{ tool.detail }}</span>
              </span>
            </motion.div>
          </div>
        </motion.article>
      </div>
    </div>
  </section>
</template>
<script setup>
import { motion } from "motion-v";

const toolGroups = [
  {
    label: "Developer Tools",
    icon: "codicon:developer-tools",
    eyebrow: "BUILD / SHIP",
    accent: "blue",
    description: "The everyday systems I use to turn ideas into reliable, polished products.",
    tools: [
      { name: "Git & GitHub", detail: "Version control" },
      { name: "VS Code", detail: "Development environment" },
      { name: "Postman", detail: "API workflows" },
      { name: "Figma", detail: "Product design" },
      { name: "Jira", detail: "Team delivery" },
      { name: "Vite", detail: "Fast tooling" },
    ],
  },
  {
    label: "AI Tools",
    icon: "ix:ai",
    eyebrow: "AUGMENT / CREATE",
    accent: "purple",
    description:
      "AI-assisted tools that help me explore faster, automate the routine, and build smarter experiences.",
    tools: [
      { name: "GitHub Copilot", detail: "Code assistance" },
      { name: "ChatGPT", detail: "Ideation & research" },
      { name: "Claude", detail: "AI assistance" },
      { name: "Cursor", detail: "AI-powered development" },
      { name: "Gemini", detail: "AI assistance" },
      { name: "Replit AI", detail: "Rapid prototyping" },
    ],
  },
];
</script>
