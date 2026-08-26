<template>
  <footer class="py-8 border-t border-slate-800/50 bg-slate-950">
    <div
      class="container mx-auto px-6 text-center text-slate-500 text-sm font-mono flex flex-col md:flex-row justify-between items-center gap-4"
    >
      <div>
        &copy; {{ new Date().getFullYear() }} Venkateswarlu Tiruveedula. All rights reserved.
      </div>
      <p class="text-slate-500">
        > Built by
        <span
          class="cursor-pointer transition-all duration-300 hover:bg-gradient-to-r hover:from-blue-500 hover:to-purple-500 hover:bg-clip-text hover:text-transparent"
          >Venkateswarlu</span
        >
      </p>
      <div class="flex gap-4">
        <span class="hover:text-blue-400 cursor-pointer transition-colors">SYS.STATUS: ONLINE</span>
        <span class="text-slate-700">|</span>
        <span class="hover:text-purple-400 cursor-pointer transition-colors">V.2.0.4</span>
      </div>
    </div>
  </footer>
</template>
