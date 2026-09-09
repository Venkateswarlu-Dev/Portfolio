<template>
  <div class="absolute inset-0 overflow-hidden">
    <!-- Animated gradient orbs  -->
    <div
      class="absolute top-1/4 left-1/4 w-96 h-96 rounded-full bg-blue-600/20 blur-[120px] animate-pulse"
      :style="{ animationDuration: '4s' }"
    />
    <div
      class="absolute bottom-1/4 right-1/4 w-96 h-96 rounded-full bg-purple-600/20 blur-[120px] animate-pulse"
      :style="{ animationDuration: '6s', animationDelay: '1s' }"
    />
    <div
      class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[600px] h-[600px] rounded-full bg-blue-900/10 blur-[160px] animate-pulse"
      :style="{ animationDuration: '8s', animationDelay: '2s' }"
    />

    <!-- Cyber grid -->
    <div
      class="absolute inset-0 opacity-10"
      :style="{
        backgroundImage: `
          linear-gradient(rgba(59,130,246,0.3) 1px, transparent 1px),
          linear-gradient(90deg, rgba(59,130,246,0.3) 1px, transparent 1px)
        `,
        backgroundSize: '60px 60px',
        maskImage: 'radial-gradient(ellipse at center, black 40%, transparent 80%)',
      }"
    />

    <!-- Diagonal scan lines -->
    <div
      class="absolute inset-0 opacity-5"
      :style="{
        backgroundImage:
          'repeating-linear-gradient(0deg, transparent, transparent 2px, rgba(59,130,246,0.1) 2px, rgba(59,130,246,0.1) 4px)',
      }"
    />

    <!-- Corner accents -->
    <div class="absolute top-8 left-3 sm:left-6 w-16 h-16 border-t-2 border-l-2 border-blue-500/50" />
    <div class="absolute top-8 right-3 sm:right-6 w-16 h-16 border-t-2 border-r-2 border-purple-500/50" />
    <div class="absolute bottom-3 sm:bottom-8 left-3 sm:left-6 w-16 h-16 border-b-2 border-l-2 border-purple-500/50" />
    <div class="absolute bottom-3 sm:bottom-8 right-3 sm:right-6 w-16 h-16 border-b-2 border-r-2 border-blue-500/50" />

    <!-- Floating data nodes -->
    <div
      v-for="(node, index) in nodes"
      :key="index"
      class="absolute rounded-full"
      :style="{
        width: node.size + 'px',
        height: node.size + 'px',
        top: node.top + '%',
        left: node.left + '%',
        background: index % 2 === 0 ? 'rgba(59,130,246,0.6)' : 'rgba(139,92,246,0.6)',
        boxShadow:
          index % 2 === 0 ? '0 0 8px rgba(59,130,246,0.8)' : '0 0 8px rgba(139,92,246,0.8)',
        animation: `nodePulse ${3 + (index % 4)}s ease-in-out infinite`,
        animationDelay: `${index * 0.4}s`,
      }"
    />
  </div>
</template>

<script setup>
const nodes = Array.from({ length: 12 }, () => ({
  size: Math.random() * 4 + 2,
  top: Math.random() * 100,
  left: Math.random() * 100,
}));
</script>

<style>
@keyframes nodePulse {
  0%,
  100% {
    opacity: 0.2;
    transform: scale(1);
  }
  50% {
    opacity: 1;
    transform: scale(1.5);
  }
}
</style>
