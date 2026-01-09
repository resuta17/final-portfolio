<script setup>
import { ref, onMounted } from 'vue'

const titles = [
  'QA Engineer',
  'Web Developer',
  'Frontend Developer',
  'QA Automation',
  'Backend Developer',
]

const currentText = ref('')
let currentTitleIndex = 0
let charIndex = 0

function typeWriter() {
  const fullText = titles[currentTitleIndex]

  if (charIndex < fullText.length) {
    currentText.value += fullText.charAt(charIndex)
    charIndex++
    setTimeout(typeWriter, 100)
  } else {
    setTimeout(() => eraseText(), 1500)
  }
}

function eraseText() {
  if (charIndex > 0) {
    currentText.value = currentText.value.slice(0, charIndex - 1)
    charIndex--
    setTimeout(eraseText, 50)
  } else {
    currentTitleIndex = (currentTitleIndex + 1) % titles.length
    setTimeout(typeWriter, 500)
  }
}

onMounted(() => {
  typeWriter()
})
</script>

<template>
  <div class="relative min-h-screen bg-slate-950 text-white overflow-hidden">
    <div class="glow-layer">
      <span v-for="i in 4" :key="i" class="glow"></span>
    </div>
    <section
      class="relative flex flex-col justify-center items-center min-h-screen text-center px-6"
    >
      <div class="flex min-w-screen min-h-screen">
        <div class="w-1/2 text-white flex items-center justify-center">
          <div class="relative inline-block">
            <div class="neon-bg"></div>
            <img
              src="./assets/JustME.png"
              width="350"
              height="350"
              class="relative z-10 border-b-4 border-teal-[rgba(45, 212, 191, 0.9)]"
            />
          </div>
        </div>
        <div class="w-1/2 text-white flex items-center justify-start text-start pr-20">
          <div class="font-poppins">
            <span class="text-2xl md:text-2xl"> Hi, I'm</span> <br />
            <span class="text-teal-400 text-2xl md:text-4xl font-bold">John Lester H. Hebres</span
            ><br />
            <span class="text-2xl md:text-xl"
              >And I'm looking for an entry-level job as a
              <span class="text-teal-600 font-bold">{{ currentText }}</span>
              <span class="text-teal-600 animate-blink">|</span></span
            >
            <p class="mt-2">
              <span class="text-gray-400 leading-[2rem]">
                Computer Science graduate seeking an entry-level Web Developer, QA Engineer,
                Backend/Frontend Developer, or other entry-level IT position where I can apply my
                technical skills, learn quickly, and contribute to organizational success.
              </span>
            </p>
          </div>
        </div>
      </div>

      <div class="absolute bottom-10 flex flex-col items-center animate-bounce">
        <span class="text-gray-400 mb-2">Scroll Down</span>
        <svg
          class="w-6 h-6 text-gray-400"
          fill="none"
          stroke="currentColor"
          stroke-width="2"
          viewBox="0 0 24 24"
        >
          <path stroke-linecap="round" stroke-linejoin="round" d="M19 9l-7 7-7-7" />
        </svg>
      </div>
    </section>

    <!-- Next Section (content hidden until scroll) -->
    <section class="min-h-screen bg-gray-900 flex justify-center items-center text-white text-3xl">
      TEST CONTENT
    </section>
  </div>
</template>

<style>
.glow-layer {
  position: fixed;
  inset: 0;
  pointer-events: none;
  z-index: 0;
}

.glow {
  position: absolute;
  width: 200px;
  height: 200px;
  filter: blur(110px);
  border-radius: 50%;
  background: rgba(45, 212, 191, 0.55);
  animation: float 30s infinite alternate ease-in-out;
}

.glow:nth-child(1) {
  top: 10%;
  left: 20%;
  animation-duration: 28s;
}
.glow:nth-child(2) {
  top: 40%;
  left: 90%;
  animation-duration: 32s;
}
.glow:nth-child(3) {
  top: 70%;
  left: 20%;
  animation-duration: 26s;
}
.glow:nth-child(4) {
  top: 20%;
  left: 100%;
  animation-duration: 34s;
}
.neon-bg {
  position: absolute;
  inset: 20px;
  border-radius: 24px;
  background: rgba(45, 212, 191, 0.9);

  box-shadow:
    0 0 20px rgba(45, 212, 191, 0.7),
    0 0 40px rgba(45, 212, 191, 0.5),
    0 0 60px rgba(45, 212, 191, 0.4),
    0 0 100px rgba(45, 212, 191, 0.3);

  filter: blur(1px);
  z-index: 0;
}

@keyframes float {
  from {
    transform: translate(-40px, -40px);
  }
  to {
    transform: translate(40px, 40px);
  }
}

html {
  scroll-behavior: smooth;
}

@keyframes blink {
  0%,
  50%,
  100% {
    opacity: 1;
  }
  25%,
  75% {
    opacity: 0;
  }
}

.animate-blink {
  display: inline-block;
  animation: blink 1s infinite;
}
</style>
