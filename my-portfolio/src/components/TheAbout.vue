<template>
  <!-- Background: Grey (#a2a7b0) matching your image -->
  <section id="about" class="w-full py-20 px-6 md:px-20 bg-[#9ca3af] font-poppins overflow-hidden">
    
    <!-- Main Heading Container -->
    <div class="text-center mb-12">
      
      <!-- 
         HEADING ANIMATION:
         :class="activeTextClass" -> Ye Text ka color change karega.
      -->
      <h2 
        class="text-3xl md:text-4xl font-bold inline-block relative transition-colors duration-500 ease-in-out"
        :class="activeTextClass"
      >
        About Me
        
        <!-- 
           LINE ANIMATION:
           :class="activeBgClass" -> Ye Line ka color change karega.
        -->
        <span 
          class="absolute -bottom-3 left-1/2 -translate-x-1/2 w-12 h-1 rounded-full transition-colors duration-500 ease-in-out"
          :class="activeBgClass"
        ></span>

      </h2>
    </div>

    <div class="flex flex-col md:flex-row items-center gap-10 md:gap-16 max-w-6xl mx-auto">
      
      <!-- LEFT SIDE: Text Content -->
      <div class="flex-1 order-2 md:order-1">
        <h3 class="text-2xl md:text-3xl font-bold text-white mb-4 leading-tight">
          Front End Developer "Specialized in Vue.js"
        </h3>

        <p class="text-gray-100 text-base mb-4 leading-relaxed">
          I'm a passionate front-end developer with  creating modern, responsive web applications. I specialize in React.js, Next.js, and creating seamless user experiences.
        </p>

        <p class="text-gray-100 text-base mb-6 leading-relaxed">
          My expertise includes HTML5, TailwindCSS, Bootstrap, Git, and GitHub. I also have experience developing with Vue.js to enhance browser functionality.
        </p>

        <div class="flex flex-wrap gap-2">
          <span 
            v-for="(skill, index) in skills" 
            :key="index"
            class="bg-white/90 text-slate-800 px-5 py-2 rounded-full shadow-sm font-medium text-sm cursor-pointer transition-all duration-300 hover:bg-brand-green hover:text-white hover:-translate-y-1"
          >
            {{ skill }}
          </span>
        </div>
      </div>

      <!-- RIGHT SIDE: Image Box -->
      <div class="flex-1 order-1 md:order-2 w-full flex justify-center md:justify-end">
        <div class="relative w-full max-w-[400px] h-[480px] rounded-2xl overflow-hidden border-[3px] border-white/40 shadow-[0_0_30px_rgba(46,204,113,0.4)] hover:shadow-[0_0_60px_rgba(46,204,113,0.7)] transition-shadow duration-500 bg-white/5">
          <img 
            src="../assets/about.jpg" 
            alt="About Me" 
            class="w-full h-full object-cover object-top hover:scale-105 transition-transform duration-700" 
          />
        </div>
      </div>

    </div>
  </section>
</template>

<script setup>
import { ref, onMounted, onUnmounted, computed } from 'vue';

const skills = ['Next.JS', 'React.JS', 'HTML5', 'TailwindCSS', 'Bootstrap', 'Git', 'GitHub', 'Vue.js'];

// 1. Text Colors Array (Heading k liye)
const textSteps = ['text-brand-green', 'text-red-500', 'text-white'];

// 2. Background Colors Array (Line k liye) - Same sequence
const bgSteps = ['bg-brand-green', 'bg-red-500', 'bg-white'];

const currentIndex = ref(0);
let intervalId = null;

// Computed Properties: Ye current color utha kar HTML ko dengi
const activeTextClass = computed(() => textSteps[currentIndex.value]);
const activeBgClass = computed(() => bgSteps[currentIndex.value]);

onMounted(() => {
  // Har 4 second baad index badal jayega
  intervalId = setInterval(() => {
    currentIndex.value = (currentIndex.value + 1) % textSteps.length;
  }, 4000);
});

onUnmounted(() => {
  if (intervalId) clearInterval(intervalId);
});
</script>