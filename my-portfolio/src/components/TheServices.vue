<template>
  <section id="services" class="w-full py-20 px-6 md:px-20 bg-[#9ca3af] font-poppins">
    
    <!-- Heading Section -->
    <div class="text-center mb-16">
      
      <!-- Main Heading Container -->
      <h2 class="text-3xl md:text-4xl font-bold inline-block relative">
        
        <!-- 
           SHINE WRAPPER:
           Is 'span' par 'overflow-hidden' lagaya hai.
           Ab light sirf iskay andar rahay gi, bahar nahi jayegi.
        -->
        <span class="relative overflow-hidden inline-block py-2 px-1">
          
          <!-- Text Content -->
          <span class="text-white mr-2 relative z-10">My</span>
          <span 
            class="transition-colors duration-500 relative z-10"
            :class="isRed ? 'text-red-600' : 'text-brand-green'"
          >
            Services
          </span>

          <!-- 
             THE SHINE ELEMENT:
             1. 'bg-white/30': Opacity 30% kar di (Halki c light).
             2. 'animate-shine-subtle': Ye text k andar hi guzregi.
          -->
          <div class="absolute top-0 -left-[100%] w-full h-full bg-gradient-to-r from-transparent via-white/40 to-transparent -skew-x-12 animate-shine-subtle"></div>

        </span>

        <!-- Decorative Line (Wrapper k bahar hai taake katay na) -->
        <span 
          class="absolute bottom-0 left-1/2 -translate-x-1/2 w-16 h-1 rounded-full transition-colors duration-500"
          :class="isRed ? 'bg-red-600' : 'bg-brand-green'"
        ></span>
      </h2>
      
      <p class="text-gray-100 mt-4 max-w-xl mx-auto">
        I provide high-quality web development services to help your business grow.
      </p>
    </div>

    <!-- Services Grid -->
    <div class="grid grid-cols-1 md:grid-cols-3 gap-8 max-w-7xl mx-auto">
      
      <div 
        v-for="(service, index) in services" 
        :key="index"
        class="group relative bg-white rounded-2xl overflow-hidden shadow-lg hover:shadow-2xl transition-all duration-300 hover:-translate-y-2 p-8"
      >
        
        <!-- Green Layer Animation -->
        <div class="absolute top-0 left-0 w-full h-0 bg-brand-green transition-all duration-500 ease-out group-hover:h-full"></div>

        <!-- Content -->
        <div class="relative z-10 group-hover:text-white transition-colors duration-300">
          
          <div class="w-14 h-14 mb-6 bg-green-50 rounded-lg flex items-center justify-center text-brand-green group-hover:bg-white group-hover:text-brand-green transition-all duration-300 shadow-sm">
            <div v-html="service.icon"></div>
          </div>

          <h3 class="text-2xl font-bold text-gray-800 mb-3 group-hover:text-white transition-colors duration-300">
            {{ service.title }}
          </h3>

          <p class="text-gray-500 group-hover:text-gray-100 transition-colors duration-300 leading-relaxed">
            {{ service.description }}
          </p>
        </div>

      </div>

    </div>
  </section>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue';

const services = ref([
  {
    title: 'Web Development',
    description: 'Building fast, secure, and scalable websites using modern technologies like Vue.js, React, and Tailwind CSS.',
    icon: `<svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-8 h-8"><path stroke-linecap="round" stroke-linejoin="round" d="M17.25 6.75L22.5 12l-5.25 5.25m-10.5 0L1.5 12l5.25-5.25m7.5-3l-4.5 16.5" /></svg>`
  },
  {
    title: 'Responsive Design',
    description: 'Ensuring your website looks amazing and works perfectly on all devices, from mobile phones to large desktops.',
    icon: `<svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-8 h-8"><path stroke-linecap="round" stroke-linejoin="round" d="M10.5 1.5H8.25A2.25 2.25 0 006 3.75v16.5a2.25 2.25 0 002.25 2.25h7.5A2.25 2.25 0 0018 20.25V3.75a2.25 2.25 0 00-2.25-2.25H13.5m-3 0V3h3V1.5m-3 0h3m-3 18.75h3" /></svg>`
  },
  {
    title: 'Chrome Extensions',
    description: 'Custom browser extensions to automate tasks, enhance productivity, and add new features to your browser.',
    icon: `<svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-8 h-8"><path stroke-linecap="round" stroke-linejoin="round" d="M9.53 16.122a3 3 0 00-5.78 1.128 2.25 2.25 0 01-2.4 2.245 4.5 4.5 0 008.4-2.245c0-.399-.078-.78-.22-1.128zm0 0a15.998 15.998 0 003.388-1.62m-5.043-.025a15.994 15.994 0 011.622-3.395m3.42 3.42a15.995 15.995 0 004.764-4.648l3.876-5.814a1.151 1.151 0 00-1.597-1.597L14.146 6.32a15.996 15.996 0 00-4.649 4.763m3.42 3.42a6.776 6.776 0 00-3.42-3.42" /></svg>`
  }
]);

const isRed = ref(false);
let intervalId = null;

onMounted(() => {
  intervalId = setInterval(() => {
    isRed.value = !isRed.value;
  }, 3000);
});

onUnmounted(() => {
  if (intervalId) clearInterval(intervalId);
});
</script>

<style scoped>
/* 
  SUBTLE SHINE ANIMATION
  Text k andar hi limited rahay gi aur halki hogi.
*/
.animate-shine-subtle {
  animation: shinePass 3s infinite ease-in-out;
}

@keyframes shinePass {
  0% { left: -100%; }
  40% { left: 200%; } /* Jaldi guzar jaye */
  100% { left: 200%; } /* Thora wait kare */
}
</style>