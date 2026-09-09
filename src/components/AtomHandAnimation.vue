<template>
  <div class="hero-animation">
    <div class="hand-container">
      <img src="/image.png" class="hand" alt="Hand" />
      <div class="energy-dot"></div>

      <div class="atom-wrapper">
        <div class="energy-point"></div>

        <div class="core">Web</div>
        <div class="rings">
          <div class="orbit orbit1"></div>
          <div class="orbit orbit2"></div>
          <div class="orbit orbit3"></div>
        </div>

        <div
          v-for="stat in statsData"
          :key="stat.value"
          :data-orbit="stat.orbit"
          :data-angle="stat.angle"
          class="node"
        >
          <div class="text-sm font-bold font-orbitron bg-clip-text text-slate-100">
            {{ stat.value }}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { onMounted } from "vue";
import gsap from "gsap";

const statsData = [
  {
    value: "React",
    orbit: 1,
    angle: 0,
  },
  {
    value: "Vue",
    orbit: 1,
    angle: Math.PI,
  },

  {
    value: "JS",
    orbit: 2,
    angle: Math.PI / 2,
  },
  {
    value: "TS",
    orbit: 2,
    angle: Math.PI * 1.5,
  },

  {
    value: "4Y Exp",
    orbit: 3,
    angle: Math.PI / 4,
  },
];

// GSAP can't interpolate `var(--foo)` inside a filter/color string — it needs
// a literal resolved color. This reads the custom property's computed value
// off a live element so we can hand GSAP a real hsl(...) string.
function resolveCssVar(varName, fallback) {
  const value = getComputedStyle(document.documentElement).getPropertyValue(varName).trim();
  return value ? value : fallback;
}

onMounted(() => {
  // Hide dot immediately so it doesn't flash at page bottom
  gsap.set(".energy-dot", { opacity: 0 });

  const tl = gsap.timeline();

  const primaryHsl = `hsl(${resolveCssVar("--primary", "262 83% 58%")})`;

  // ---- STEP 1: Neon Hand Appears ----
  // Opacity, scale, AND the glow now animate together in one tween instead
  // of two sequential ones. The original "shadow fading up after hand shows"
  // issue was caused by the glow being a separate tween that played out
  // *after* the fade-in finished — visually that reads as a second, delayed
  // glow bloom. Putting filter in the same fromTo as opacity/scale means the
  // glow ramps in alongside the hand becoming visible, as one motion.
  tl.fromTo(
    ".hand",
    {
      opacity: 0,
      scale: 0.92,
      x: 200,
      filter: `drop-shadow(0 0 0px ${primaryHsl})`,
    },
    {
      opacity: 1,
      scale: 1,
      x: 0,
      filter: `drop-shadow(0 0 18px ${primaryHsl})`,
      duration: 1.1,
      ease: "power3.out",
    },
  );

  // Calculate positions AFTER hand animation settles
  tl.call(() => {
    const container = document.querySelector(".hand-container");
    const handImg = document.querySelector(".hand");
    const energyPoint = document.querySelector(".energy-point");
    const dot = document.querySelector(".energy-dot");

    const containerRect = container.getBoundingClientRect();
    const handRect = handImg.getBoundingClientRect();
    const epRect = energyPoint.getBoundingClientRect();

    // Energy point center relative to container
    const epX = epRect.left + epRect.width / 2 - containerRect.left;
    const epY = epRect.top + epRect.height / 2 - containerRect.top;

    // Palm Y: ~75% down the hand image, but X locked to energy point X for straight vertical travel
    const palmY = handRect.top + handRect.height * 0.55 - containerRect.top;

    // Place dot directly below energy point (same X), at palm height
    gsap.set(dot, {
      left: epX, // ← same X as energy point = perfectly vertical path
      top: palmY,
      xPercent: -50,
      yPercent: -50,
      opacity: 0,
      x: 0,
      y: 0,
    });

    const dy = epY - palmY; // negative number (travels upward)

    gsap.to(dot, {
      y: dy, // ← only Y moves, no X offset = straight vertical
      opacity: 1,
      duration: 0.75,
      ease: "power1.in",
      onComplete: () => gsap.to(dot, { opacity: 0, duration: 0.25 }),
    });
  });

  // Energy point ignites as the beam arrives
  tl.fromTo(
    ".energy-point",
    {
      scale: 0,
      opacity: 0,
    },
    {
      scale: 1,
      opacity: 1,
      duration: 0.5,
    },
    "+=0.9",
  );

  // Core appears
  tl.to(".core", {
    scale: 1,
    opacity: 1,
    duration: 0.8,
  });

  // Rings
  tl.to(".orbit", {
    opacity: 1,
    scale: 1,
    stagger: 0.15,
    duration: 0.5,
  });

  tl.to(".orbit1", {
    opacity: 1,
    scale: 1,
    duration: 0.5,
  });

  tl.to(".orbit2", {
    opacity: 1,
    scale: 1,
    duration: 0.5,
  });

  tl.to(".orbit3", {
    opacity: 1,
    scale: 1,
    duration: 0.5,
  });

  const wrapper = document.querySelector(".atom-wrapper");
  const centerX = wrapper.offsetWidth / 2;
  const centerY = wrapper.offsetHeight / 2;

  document.querySelectorAll(".node").forEach((node) => {
    node.style.left = `${centerX}px`;
    node.style.top = `${centerY}px`;
  });

  tl.fromTo(
    ".node",
    {
      opacity: 0,
      scale: 0,
    },
    {
      opacity: 1,
      scale: 1,
      stagger: 0.15,
      duration: 0.4,
      onComplete: animateNodesToOrbit,
    },
  );
});

function moveNodeOnOrbit(el, angle, radiusX, radiusY, rotation, centerX, centerY) {
  const x = Math.cos(angle) * radiusX;
  const y = Math.sin(angle) * radiusY;

  const rotatedX = x * Math.cos(rotation) - y * Math.sin(rotation);

  const rotatedY = x * Math.sin(rotation) + y * Math.cos(rotation);

  el.style.left = `${centerX + rotatedX}px`;

  el.style.top = `${centerY + rotatedY}px`;

  const depth = Math.sin(angle);

  const scale = 0.8 + (depth + 1) * 0.15;

  el.style.transform = `translate(-50%, -50%) scale(${scale})`;

  el.style.opacity = 0.6 + (depth + 1) * 0.2;
}

function startOrbitAnimation() {
  const wrapper = document.querySelector(".atom-wrapper");

  const centerX = wrapper.offsetWidth / 2;

  const centerY = wrapper.offsetHeight / 2;

  const nodes = document.querySelectorAll(".node");

  const orbitConfig = {
    // React + Vue
    1: {
      radiusX: 200,
      radiusY: 80,
      rotation: 0,
    },

    // JS + TS
    2: {
      radiusX: 200,
      radiusY: 80,
      rotation: Math.PI / 3,
    },

    // Exp
    3: {
      radiusX: 200,
      radiusY: 80,
      rotation: (Math.PI / 3) * 2,
    },
  };

  gsap.ticker.add(() => {
    nodes.forEach((node, index) => {
      const orbit = Number(node.dataset.orbit);

      const config = orbitConfig[orbit];

      if (!config) return;

      let angle = Number(node.dataset.angle);

      if (orbit === 1) angle += 0.003;

      if (orbit === 2) angle += 0.0025;

      if (orbit === 3) angle += 0.002;

      node.dataset.angle = angle;

      moveNodeOnOrbit(
        node,
        angle,

        config.radiusX,
        config.radiusY,

        config.rotation,

        centerX,
        centerY,
      );
    });
  });
}

function animateNodesToOrbit() {
  const wrapper = document.querySelector(".atom-wrapper");

  const centerX = wrapper.offsetWidth / 2;
  const centerY = wrapper.offsetHeight / 2;

  const nodes = document.querySelectorAll(".node");

  const orbitConfig = {
    1: {
      radiusX: 200,
      radiusY: 80,
      rotation: 0,
    },

    2: {
      radiusX: 200,
      radiusY: 80,
      rotation: Math.PI / 3,
    },

    3: {
      radiusX: 200,
      radiusY: 80,
      rotation: (Math.PI / 3) * 2,
    },
  };

  nodes.forEach((node) => {
    const orbit = Number(node.dataset.orbit);
    const angle = Number(node.dataset.angle);

    const config = orbitConfig[orbit];

    const x = Math.cos(angle) * config.radiusX;
    const y = Math.sin(angle) * config.radiusY;

    const rotatedX = x * Math.cos(config.rotation) - y * Math.sin(config.rotation);

    const rotatedY = x * Math.sin(config.rotation) + y * Math.cos(config.rotation);

    gsap.to(node, {
      left: centerX + rotatedX,
      top: centerY + rotatedY,
      duration: 1.2,
      ease: "power2.out",
    });
  });

  gsap.delayedCall(1.3, () => startOrbitAnimation());
}
</script>

<style scoped>
.hero-animation {
  position: relative;
  width: 100%;
  /* Mobile/tablet: the hero stacks vertically (text above, animation
     below), so this only needs enough height to show the animation
     itself — not a full screen's worth. */
  height: 60vh;
  min-height: 320px;
  overflow: hidden;
}

.hand-container {
  position: absolute;
  right: 0;
  bottom: 0;
  width: min(420px, 75vw);
}

/* @media (max-width: 480px) {
  .hero-animation {
    height: 42vh;
    min-height: 280px;
  }

  .hand-container {
    width: min(340px, 85vw);
  }

  .atom-wrapper {
    left: auto;
    top: auto;
    right: -10%;
    bottom: 8%;
    transform: scale(0.55);
  }
} */

@media (min-width: 481px) and (max-width: 768px) {
  .hero-animation {
    width: 100%;
    height: 420px;
    overflow: hidden;
  }

  .hand-container {
    position: absolute;
    left: 50%;
    right: auto;
    bottom: 0;
    width: min(420px, 90vw);
    transform: translateX(-50%);
  }

  .atom-wrapper {
    left: 50%;
    right: auto;
    top: auto;
    bottom: 15%;
    transform: translateX(-50%) scale(0.65);
    transform-origin: center center;
  }
}

/* Tablet (portrait/landscape): a bit more room than phones, still
   stacked above/below the text since Hero only goes side-by-side at lg. */
@media (min-width: 640px) {
  .hero-animation {
    height: 70vh;
    min-height: 420px;
  }

  .hand-container {
    width: min(560px, 65vw);
  }
}

/* Desktop/laptop and up: back to the original full-height, side-by-side
   layout (Hero switches to flex-row at lg / 1024px). */
@media (min-width: 1024px) {
  .hero-animation {
    height: 100vh;
    min-height: 0;
  }

  .hand-container {
    width: min(700px, 55vw);
  }
}

/* 4K / large monitors: let the whole animation scale up a little so it
   doesn't look small next to the larger hero text. */
@media (min-width: 2560px) {
  .hand-container {
    width: min(900px, 45vw);
  }
}

/* HAND */
.hand {
  display: block;
  width: 100%;
}

.energy-dot {
  position: absolute;
  width: 20px;
  height: 20px;
  will-change: transform, opacity;
}

/* Outer halo */
.energy-dot::before {
  content: "";
  position: absolute;
  inset: -25px;
  border-radius: 50%;
  background: radial-gradient(circle, rgba(255, 255, 255, 0.12) 0%, transparent 70%);
  animation: halo-pulse 2s ease-in-out infinite;
}

.energy-dot::after {
  content: "";
  position: absolute;
  inset: 0;
  border-radius: 50%;
  background: #fff;
  box-shadow:
    0 0 4px rgba(255, 255, 255, 1),
    0 0 10px rgba(255, 255, 255, 0.95),
    0 0 20px rgba(255, 255, 255, 0.8),
    0 0 40px rgba(255, 255, 255, 0.6),
    0 0 80px rgba(255, 255, 255, 0.3);
  animation: core-pulse 1.5s ease-in-out infinite;
}

@keyframes core-pulse {
  0% {
    transform: scale(1);
  }

  50% {
    transform: scale(1.25);
  }

  100% {
    transform: scale(1);
  }
}

@keyframes halo-pulse {
  0% {
    transform: scale(0.8);
    opacity: 0.5;
  }

  50% {
    transform: scale(1.3);
    opacity: 1;
  }

  100% {
    transform: scale(0.8);
    opacity: 0.5;
  }
}

/* ATOM */
.atom-wrapper {
  position: absolute;
  left: 15%;
  top: -25%;
  width: 320px;
  height: 320px;
  transform: scale(0.85);
}

/* ENERGY */
.energy-point {
  position: absolute;
  left: 50%;
  top: 50%;
  width: 10px;
  height: 10px;
  border-radius: 50%;
  background: hsl(var(--primary));
  transform: translate(-50%, -50%);
  box-shadow:
    0 0 15px hsl(var(--primary)),
    0 0 40px hsl(var(--primary));
}

/* CORE */
.core {
  position: absolute;
  left: 50%;
  top: 50%;
  width: 100px;
  height: 100px;
  border-radius: 50%;
  background: radial-gradient(circle, hsl(var(--secondary)), hsl(var(--primary)));
  color: hsl(var(--primary-foreground));
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  font-weight: 600;
  font-size: 20px;
  font-family: "Orbitron", sans-serif;
  transform: translate(-50%, -50%) scale(0);
  opacity: 0;
  box-shadow:
    0 0 30px hsla(var(--secondary)),
    0 0 60px hsla(var(--primary));
}

/* ORBITS */
.orbit {
  position: absolute;
  left: 50%;
  top: 50%;
  width: 400px;
  height: 160px;
  border: 2px solid hsl(var(--secondary));
  border-radius: 50%;
  opacity: 0;
  transform-origin: center center;
  transform: translate(-50%, -50%) scale(0.8);
}

.orbit1 {
  transform: translate(-50%, -50%) rotate(0deg);
}

.orbit2 {
  transform: translate(-50%, -50%) rotate(60deg);
}

.orbit3 {
  transform: translate(-50%, -50%) rotate(120deg);
}

/* NODES */
.node {
  position: absolute;
  padding: 4px;
  width: 60px;
  height: 60px;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.05);
  backdrop-filter: blur(12px);
  border: 1px solid rgba(255, 255, 255, 0.1);
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  transition: all 300ms ease;
  opacity: 0;
  transform: translate(-50%, -50%);
}

.node:hover {
  transform: scale(1.05);
  border-color: rgba(139, 92, 246, 0.6);
  box-shadow: 0 0 20px rgba(59, 130, 246, 0.15);
}

/* MOBILE */
/* @media (max-width: 768px) {
  .hand-container {
    left: 50%;
    right: auto;
    bottom: 0;
    transform: translateX(-50%);
    width: min(420px, 90vw);
  }

  .atom-wrapper {
    left: auto;
    top: auto;
    right: 2%;
    bottom: 18%;
    transform: scale(0.7);
  }
} */

@media (max-width: 480px) {
  .hero-animation {
    width: 100%;
    height: 360px;
    overflow: hidden;
  }

  .hand-container {
    position: absolute;
    left: 50%;
    right: auto;
    bottom: 5%;
    transform: translateX(-50%);
    width: min(340px, 92vw);
  }

  .atom-wrapper {
    left: 50%;
    right: auto;
    top: auto;
    /* right: -10%; */
    bottom: 30%;
    transform: translateX(-50%) scale(0.55);
    transform-origin: center center;
  }
}

/* 4K / large monitors: scale the atom up a bit so it doesn't look tiny
   inside the much bigger hand-container defined above. */
@media (min-width: 2560px) {
  .atom-wrapper {
    transform: scale(1.15);
  }
}
</style>
