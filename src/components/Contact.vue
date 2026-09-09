<template>
  <section id="contact" class="py-12 md:py-16 relative">
    <div class="container mx-auto px-4 sm:px-6 lg:px-8">
      <motion.div
        :initial="{ opacity: 0, y: 30 }"
        :whileInView="{ opacity: 1, y: 0 }"
        :viewport="{ once: true }"
        :transition="{ duration: 0.6 }"
      >
        <h2 class="text-2xl sm:text-3xl md:text-5xl font-orbitron mb-8 md:mb-10 flex items-center gap-4">
          <span class="text-blue-500">06.</span> Contact
          <div class="h-px bg-slate-800 flex-grow ml-4"></div>
        </h2>
      </motion.div>

      <div class="grid md:grid-cols-2 gap-10 md:gap-16">
        <motion.div
          :initial="{ opacity: 0, x: -30 }"
          :whileInView="{ opacity: 1, x: 0 }"
          :viewport="{ once: true }"
          :transition="{ duration: 0.6, delay: 0.2 }"
        >
          <h3 class="text-2xl font-orbitron text-white mb-6">Initialize Connection</h3>
          <div class="mb-6 flex items-center gap-2">
            <span class="w-2 h-2 rounded-full bg-blue-400 animate-pulse"></span>
            <span class="font-mono font-medium">OPEN TO OPPORTUNITIES</span>
          </div>
          <p class="text-slate-400 mb-8 leading-relaxed">
            Currently open to new opportunities. Whether you have a question or just want to say hi,
            my inbox is always open.
          </p>

          <div class="space-y-6">
            <a
              href="mailto:tiruveedivenkatesh78@gmail.com"
              class="flex items-center gap-4 min-w-0 text-slate-300 hover:text-blue-400 transition-colors group"
            >
              <div
                class="w-12 h-12 shrink-0 glass-card rounded flex items-center justify-center group-hover:neon-box-blue transition-all"
              >
                <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path
                    strokeLinecap="round"
                    strokeLinejoin="round"
                    strokeWidth="2"
                    d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"
                  ></path>
                </svg>
              </div>
              <span class="font-mono text-xs sm:text-sm break-all"
                >venkateswarlu.tiruveedula.dev@gmail.com</span
              >
            </a>
            <a
              href="https://www.linkedin.com/in/venkateswarlu-tiruveedula-327a95218"
              target="_blank"
              rel="noopener noreferrer"
              class="flex items-center gap-4 min-w-0 text-slate-300 hover:text-purple-400 transition-colors group"
            >
              <div
                class="w-12 h-12 shrink-0 glass-card rounded flex items-center justify-center group-hover:neon-box-purple transition-all"
              >
                <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24">
                  <path
                    d="M19 0h-14c-2.761 0-5 2.239-5 5v14c0 2.761 2.239 5 5 5h14c2.762 0 5-2.239 5-5v-14c0-2.761-2.238-5-5-5zm-11 19h-3v-11h3v11zm-1.5-12.268c-.966 0-1.75-.79-1.75-1.764s.784-1.764 1.75-1.764 1.75.79 1.75 1.764-.783 1.764-1.75 1.764zm13.5 12.268h-3v-5.604c0-3.368-4-3.113-4 0v5.604h-3v-11h3v1.765c1.396-2.586 7-2.777 7 2.476v6.759z"
                  />
                </svg>
              </div>
              <span class="font-mono text-xs sm:text-sm break-all">Venkateswarlu Tiruveedula</span>
            </a>
            <a
              href="https://github.com/Venkateswarlu-Dev"
              target="_blank"
              rel="noopener noreferrer"
              class="flex items-center gap-4 min-w-0 text-slate-300 hover:text-white transition-colors group"
            >
              <div
                class="w-12 h-12 shrink-0 glass-card rounded flex items-center justify-center group-hover:border-slate-500 transition-all"
              >
                <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24">
                  <path
                    d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"
                  />
                </svg>
              </div>
              <span class="font-mono text-xs sm:text-sm break-all">Venkateswarlu-Dev</span>
            </a>
          </div>
        </motion.div>

        <motion.div
          :initial="{ opacity: 0, x: 30 }"
          :whileInView="{ opacity: 1, x: 0 }"
          :viewport="{ once: true }"
          :transition="{ duration: 0.6, delay: 0.4 }"
          class="glass-card p-5 sm:p-8 rounded-xl flex items-center justify-center"
        >
          <div v-if="status && statusType === 'success'" class="text-center py-10">
            <div class="text-green-400 font-mono text-lg mb-3">{{ status }}</div>
            <p class="text-slate-400 text-md">
              Thanks for reaching out. I've received your message and will get back to you soon.
            </p>
            <button
              @click="
                status = '';
                statusType = '';
              "
              class="mt-3 text-sm font-mono text-blue-400 hover:text-purple-400 transition-colors"
            >
              > SEND ANOTHER MESSAGE
            </button>
          </div>
          <form v-else @submit.prevent="submitForm" class="flex flex-col gap-6 w-full">
            <div>
              <label htmlFor="" class="block text-sm font-mono text-slate-400 mb-2">_NAME</label>
              <input
                v-model="form.name"
                type="text"
                id="name"
                name="name"
                class="w-full bg-slate-950/50 border border-slate-800 rounded px-4 py-3 text-white focus:outline-none focus:border-blue-500 focus:ring-1 focus:ring-blue-500 transition-all"
                required
                data-testid="input-name"
              />
            </div>
            <div>
              <label htmlFor="email" class="block text-sm font-mono text-slate-400 mb-2"
                >_EMAIL</label
              >
              <input
                v-model="form.email"
                type="email"
                id="email"
                name="email"
                class="w-full bg-slate-950/50 border border-slate-800 rounded px-4 py-3 text-white focus:outline-none focus:border-blue-500 focus:ring-1 focus:ring-blue-500 transition-all"
                required
                data-testid="input-email"
              />
            </div>
            <div>
              <label htmlFor="message" class="block text-sm font-mono text-slate-400 mb-2"
                >_MESSAGE</label
              >
              <textarea
                v-model="form.message"
                id="message"
                name="message"
                rows="4"
                class="w-full bg-slate-950/50 border border-slate-800 rounded px-4 py-3 text-white focus:outline-none focus:border-blue-500 focus:ring-1 focus:ring-blue-500 transition-all resize-none"
                required
                data-testid="input-message"
              ></textarea>
            </div>
            <button
              type="submit"
              :disabled="isSubmitting"
              class="w-full py-4 bg-blue-600/20 border border-blue-500 text-blue-400 font-orbitron rounded hover:bg-blue-600 hover:text-white transition-all duration-300 neon-box-blue"
              data-testid="btn-submit-contact"
            >
              {{ isSubmitting ? "Transmitting..." : "Transmit Message" }}
            </button>
            <p
              v-if="status && statusType !== 'success'"
              class="text-sm font-mono mt-2"
              :class="{
                'text-blue-400': statusType === 'loading',
                'text-red-400': statusType === 'error',
              }"
            >
              > {{ status }}
            </p>
          </form>
        </motion.div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { motion } from "motion-v";
import { ref } from "vue";

const form = ref({
  name: "",
  email: "",
  message: "",
});

const isSubmitting = ref(false);
const status = ref("");
const statusType = ref("");

const submitForm = async () => {
  isSubmitting.value = true;
  status.value = "Transmitting...";
  statusType.value = "loading";

  try {
    const response = await fetch("https://formspree.io/f/maewabvp", {
      method: "POST",
      headers: {
        "Content-Type": "application/json",
      },
      body: JSON.stringify(form.value),
    });

    const result = await response.json();

    if (response.ok) {
      status.value = "✓ Message Transmitted";
      statusType.value = "success";
      form.value = {
        name: "",
        email: "",
        message: "",
      };
    } else {
      status.value =
        result.errors[0].message.charAt(0).toUpperCase() + result.errors[0].message.slice(1) ||
        "✕ Transmission Failed";
      statusType.value = "error";
    }
  } catch (error) {
    status.value = "✕ Connection Error";
    statusType.value = "error";
  } finally {
    isSubmitting.value = false;
  }
};
</script>