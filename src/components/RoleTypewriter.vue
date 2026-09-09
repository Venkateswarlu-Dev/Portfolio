<template>
  <span
    class="text-transparent bg-clip-text bg-gradient-to-br from-blue-400 to-purple-500 border-r-2 border-purple-400 pr-1 animate-pulse"
    aria-live="polite"
    >{{ displayText }}</span
  >
</template>

<script setup>
import { onBeforeUnmount, onMounted, ref } from "vue";

const typingRoles = ["Frontend Developer", "Vue & Nuxt Developer", "React.js Developer", "AI Enthusiast"];

const displayText = ref("");
let roleIndex = 0;
let charIndex = 0;
let deleting = false;
let timerId = 0;

function tick() {
  const role = typingRoles[roleIndex] ?? "";
  displayText.value = role.slice(0, Math.max(0, charIndex));

  if (!deleting && charIndex <= role.length) {
    charIndex += 1;
    timerId = window.setTimeout(tick, charIndex === role.length + 1 ? 1200 : 72);
    return;
  }

  if (deleting && charIndex >= 0) {
    charIndex -= 1;
    timerId = window.setTimeout(tick, 34);
    return;
  }

  deleting = !deleting;
  if (!deleting) {
    roleIndex = (roleIndex + 1) % typingRoles.length;
    charIndex = 0;
  }
  timerId = window.setTimeout(tick, 240);
}

onMounted(() => {
  if (window.matchMedia("(prefers-reduced-motion: reduce)").matches) {
    displayText.value = typingRoles.join(" | ");
    return;
  }

  tick();
});

onBeforeUnmount(() => {
  window.clearTimeout(timerId);
});
</script>