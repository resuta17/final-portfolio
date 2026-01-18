<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const isScrolled = ref(false)
const handleScroll = () => {
  isScrolled.value = window.scrollY > 0
}
onMounted(() => window.addEventListener('scroll', handleScroll))
onUnmounted(() => window.removeEventListener('scroll', handleScroll))

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

onMounted(() => typeWriter())
</script>

<template>
  <div class="relative bg-slate-950 text-white min-h-screen">
    <div class="glow-layer">
      <span v-for="i in 5" :key="i" class="glow"></span>
    </div>

    <nav
      class="sticky top-0 z-50 h-10 bg-slate-950/0 backdrop-blur-xl flex justify-between px-10 items-center transition-all duration-500"
      :class="{ 'border-b-1 border-white/20': isScrolled }"
    >
      <div><p class="font-sans font-bold text-teal-400 shiny-text">JL Hebres</p></div>
      <div class="text-teal-400 px-2 text-sm items-center flex justify-center space-x-6">
        <div>Projects</div>
        <div>Experience</div>
        <div>Skills</div>
        <div>About Me</div>
      </div>
      <button
        class="text-teal-400 px-2 text-xs border-1 rounded-full hover:cursor-pointer hover:bg-teal-900"
      >
        Download CV
      </button>
    </nav>

    <section
      class="relative flex flex-col md:flex-row justify-center items-center min-h-screen px-6 z-10"
    >
      <div class="w-full md:w-1/2 flex justify-center items-center">
        <div class="relative inline-block">
          <div class="neon-bg"></div>
          <img
            src="./assets/JustME.png"
            width="350"
            height="350"
            class="relative z-10 border-b-4 border-teal-[rgba(45,212,191,0.9)]"
          />
        </div>
      </div>

      <div class="w-full md:w-1/2 flex flex-col items-start text-start px-6 md:pr-20 mt-10 md:mt-0">
        <span class="text-2xl md:text-2xl">Hi, I'm</span>
        <span class="text-teal-400 text-2xl md:text-4xl font-bold">John Lester H. Hebres</span>
        <span class="text-2xl md:text-xl">
          And I'm looking for an entry-level job as a
          <span class="text-teal-600 font-bold">{{ currentText }}</span>
          <span class="text-teal-600 animate-blink">|</span>
        </span>
        <p class="mt-4 text-gray-400 leading-[2rem]">
          Computer Science graduate seeking an entry-level Web Developer, QA Engineer,
          Backend/Frontend Developer, or other entry-level IT position where I can apply my
          technical skills, learn quickly, and contribute to organizational success.
        </p>

        <div class="mt-6 flex space-x-4">
          <a href="mailto:jlhebres15@gmail.com">
            <img
              src="./assets/email-50.png"
              width="35"
              height="35"
              class="relative z-10 border-2 border-teal-400 rounded-full p-1 transition-transform duration-300 hover:bg-teal-900 hover:scale-125"
            />
          </a>
          <a href="https://www.linkedin.com/in/jlhebres/" target="_blank">
            <img
              src="./assets/linked-in-48.png"
              width="35"
              height="35"
              class="relative z-10 border-2 border-teal-400 rounded-full p-1 transition-transform duration-300 hover:bg-teal-900 hover:scale-125"
            />
          </a>
          <a href="https://github.com/resuta17" target="_blank">
            <img
              src="./assets/github-50.png"
              width="35"
              height="35"
              class="relative z-10 border-2 border-teal-400 rounded-full p-1 transition-transform duration-300 hover:bg-teal-900 hover:scale-125"
            />
          </a>
        </div>
      </div>

      <div class="absolute bottom-12 flex flex-col items-center animate-bounce z-40">
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

    <section
      class="font-poppins min-h-[90vh] bg-slate-950/60 flex flex-col justify-center items-center text-white text-3xl z-10 relative"
    >
      <p class="mt-20 text-center text-2xl text-teal-400 font-bold">Projects</p>
      <div class="flex justify-center items-center min-h-[90vh] space-x-10">
        <div
          class="h-80 w-65 bg-white/10 backdrop-blur-md rounded-xl shadow-2xl shadow-teal-900 border-2 border-teal-900 p-5"
        >
          <p class="text-center pb-4 text-md">1st Project</p>
          <p class="text-sm">BODY TEST TEXT</p>
        </div>
        <div
          class="h-80 w-65 bg-white/10 backdrop-blur-md rounded-xl shadow-2xl shadow-teal-900 border-2 border-teal-900 p-5"
        >
          <p class="text-center pb-4 text-md">2nd Project</p>
          <p class="text-sm">BODY TEST TEXT</p>
        </div>
        <div
          class="h-80 w-65 bg-white/10 backdrop-blur-md rounded-xl shadow-2xl shadow-teal-900 border-2 border-teal-900 p-5"
        >
          <p class="text-center pb-4 text-md">3rd Project</p>
          <p class="text-sm">BODY TEST TEXT</p>
        </div>

        <div
          class="h-80 w-65 bg-white/10 backdrop-blur-md rounded-xl shadow-2xl shadow-teal-900 border-2 border-teal-900 p-5"
        >
          <p class="text-center pb-4 text-md">4th Project</p>
          <p class="text-sm">BODY TEST TEXT</p>
        </div>
      </div>
    </section>

    <section class="relative justify-center items-center min-h-[90vh] px-6 z-10">
      <div>
        <p class="mt-20 text-center text-2xl text-teal-400 font-bold">Experience</p>
      </div>
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
  border-radius: 50%;
  filter: blur(110px);
  background: rgba(45, 212, 191, 0.55);
  animation: float 30s infinite alternate ease-in-out;
  opacity: 0.6;
}

.glow:nth-child(1) {
  top: 10%;
  left: 20%;
  animation-duration: 28s;
}
.glow:nth-child(2) {
  top: 50%;
  left: 80%;
  animation-duration: 32s;
}
.glow:nth-child(3) {
  top: 70%;
  left: 50%;
  animation-duration: 26s;
}
.glow:nth-child(4) {
  top: 30%;
  left: 60%;
  animation-duration: 34s;
}
.glow:nth-child(5) {
  top: 60%;
  left: 30%;
  animation-duration: 30s;
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
  animation: blink 1s infinite;
}

.shiny-text {
  text-shadow:
    0 0 5px rgba(45, 212, 191, 0.9),
    0 0 15px rgba(45, 212, 191, 0.7),
    0 0 30px rgba(45, 212, 191, 0.5),
    0 0 60px rgba(45, 212, 191, 0.3);
  animation: neon-pulse 2.5s ease-in-out infinite;
}

@keyframes neon-pulse {
  0%,
  100% {
    text-shadow:
      0 0 5px rgba(45, 212, 191, 0.8),
      0 0 15px rgba(45, 212, 191, 0.6),
      0 0 30px rgba(45, 212, 191, 0.4);
  }
  50% {
    text-shadow:
      0 0 10px rgba(45, 212, 191, 1),
      0 0 25px rgba(45, 212, 191, 0.8),
      0 0 50px rgba(45, 212, 191, 0.6);
  }
}

html {
  scroll-behavior: smooth;
}
</style>
