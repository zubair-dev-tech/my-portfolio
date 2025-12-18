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

          <p class="text-lg text-gray-500 group-hover:text-gray-100 transition-colors duration-300 leading-relaxed">
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
    title: 'Frontend Development',
    description: 'Building fast, secure, and scalable websites using modern technologies like Vue.js, React, and Tailwind CSS.',
    icon: `<svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-8 h-8"><path stroke-linecap="round" stroke-linejoin="round" d="M17.25 6.75L22.5 12l-5.25 5.25m-10.5 0L1.5 12l5.25-5.25m7.5-3l-4.5 16.5" /></svg>`
  },
  {
    title: 'Responsive Design',
    description: 'Ensuring your website looks amazing and works perfectly on all devices, from mobile phones to large desktops.',
    icon: `<svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-8 h-8"><path stroke-linecap="round" stroke-linejoin="round" d="M10.5 1.5H8.25A2.25 2.25 0 006 3.75v16.5a2.25 2.25 0 002.25 2.25h7.5A2.25 2.25 0 0018 20.25V3.75a2.25 2.25 0 00-2.25-2.25H13.5m-3 0V3h3V1.5m-3 0h3m-3 18.75h3" /></svg>`
  },
  {
    title: ' Performance & SEO',
    description: 'Optimizing websites for 100/100 Google Lighthouse scores, faster load times, and implementing SEO best practices for better ranking.',
    icon: `<svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-10 h-10">
     <path stroke-linecap="round" stroke-linejoin="round" d="M21 21l-5.197-5.197m0 0A7.5 7.5 0 105.196 5.196a7.5 7.5 0 0010.607 10.607z" />
     </svg>`
  },
  {
    id: 4,
    title: "API Integration",
    description: "Connecting frontend interfaces with backend APIs to ensure real-time data flow and secure authentication.",
    icon:  `<svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-10 h-10">
    <path stroke-linecap="round" stroke-linejoin="round" d="M20.25 6.375c0 2.278-3.694 4.125-8.25 4.125S3.75 8.653 3.75 6.375m16.5 0c0-2.278-3.694-4.125-8.25-4.125S3.75 4.097 3.75 6.375m16.5 0v11.25c0 2.278-3.694 4.125-8.25 4.125s-8.25-1.847-8.25-4.125V6.375m16.5 0v3.75m-16.5-3.75v3.75m16.5 0v3.75C20.25 16.153 16.556 18 12 18s-8.25-1.847-8.25-4.125v-3.75m16.5 0c0 2.278-3.694 4.125-8.25 4.125s-8.25-1.847-8.25-4.125" />
    </svg>`
},
{
  id: 5,
  title: "CMS Integration",
  description: "Developing dynamic content websites using Headless CMS like Sanity or Strapi for easy content management.",
  icon: `<svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-10 h-10">
  <path stroke-linecap="round" stroke-linejoin="round" d="M19.5 14.25v-2.625a3.375 3.375 0 00-3.375-3.375h-1.5A1.125 1.125 0 0113.5 7.125v-1.5a3.375 3.375 0 00-3.375-3.375H8.25m0 12.75h7.5m-7.5 3H12M10.5 2.25H5.625c-.621 0-1.125.504-1.125 1.125v17.25c0 .621.504 1.125 1.125 1.125h12.75c.621 0 1.125-.504 1.125-1.125V11.25a9 9 0 00-9-9z" />
</svg>`
},
{
  id: 6,
  title: "Bug Fixing & Support",
  description: "Debugging existing applications, fixing layout issues, and refactoring code to improve performance.",
  icon:  `<svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-10 h-10">
  <path stroke-linecap="round" stroke-linejoin="round" d="M3.75 13.5l10.5-11.25L12 10.5h8.25L9.75 21.75 12 13.5H3.75z" />
</svg>`
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