<template>
  <section id="projects" class="w-full py-20 px-6 md:px-20 bg-[#9ca3af] font-poppins">
    
    <!-- Heading -->
    <div class="text-center mb-16">
      <h2 class="text-3xl md:text-4xl font-bold inline-block relative">
        <span 
          class="transition-colors duration-700 ease-in-out mr-2"
          :class="swapColors ? 'text-brand-green' : 'text-white'"
        >My</span>
        <span 
          class="transition-colors duration-700 ease-in-out"
          :class="swapColors ? 'text-white' : 'text-brand-green'"
        >Projects</span>
        <span class="absolute -bottom-3 left-1/2 -translate-x-1/2 w-16 h-1 bg-brand-green rounded-full"></span>
      </h2>
      <!-- Naya Content -->
<p class="text-gray-200 text-base md:text-lg font-light tracking-wide max-w-2xl mx-auto mt-6 leading-relaxed">
  Explore a collection of projects where I turned ideas into <span class="text-brand-green font-medium">responsive</span> and <span class="text-brand-green font-medium">interactive</span> web reality.
</p>
    </div>

    <!-- GRID -->
    <div class="grid grid-cols-1 md:grid-cols-2 gap-8 max-w-6xl mx-auto">
      
      <div 
        v-for="(project, index) in projects" 
        :key="index"
        :id="project.id" 
        class="bg-white rounded-2xl overflow-hidden shadow-lg hover:shadow-2xl transition-all duration-300 hover:-translate-y-2 group flex flex-col"
      >
        
        <!-- Image -->
        <div class="h-55 overflow-hidden relative">
          <div class="absolute inset-0 bg-black/20 opacity-0 group-hover:opacity-100 transition-opacity duration-300 z-10"></div>
          <img 
            :src="project.image" 
            :alt="project.title" 
            class="w-full h-full object-cover transition-transform duration-500 group-hover:scale-110"
          />
        </div>

        <!-- Content -->
        <div class="p-8 flex flex-col flex-grow">
          <h3 class="text-xl font-bold text-gray-800 mb-2">{{ project.title }}</h3>
          
          <p class="text-gray-600 text-sm leading-relaxed mb-4 flex-grow">
            {{ project.description }}
          </p>

          <!-- Tags -->
          <div class="flex flex-wrap gap-2 mb-5">
            <span 
              v-for="tech in project.techStack" 
              :key="tech"
              class="text-xs font-bold text-brand-green bg-green-50 px-3 py-1 rounded-md uppercase tracking-wide border border-green-100"
            >
              {{ tech }}
            </span>
          </div>

          <!-- 
             CHANGE HERE: Button ko 'a' tag bana diya hai.
             :href="project.link" se wo link uthayega.
             target="_blank" se new tab ma open hoga.
          -->
          <a 
            :href="project.link" 
            target="_blank"
            class="custom-bounce relative overflow-hidden w-full bg-brand-green text-white px-6 py-3 rounded-full font-semibold text-sm shadow-md shadow-green-200 hover:bg-green-500 hover:shadow-lg transition-all duration-300 group/btn block text-center cursor-pointer"
          >
            <span class="relative z-10">View Project</span>
            <div class="absolute top-0 -left-[100%] w-full h-full bg-gradient-to-r from-transparent via-white/40 to-transparent -skew-x-12 group-hover/btn:animate-shine"></div>
          </a>

        </div>
      </div>

    </div>
  </section>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue';

const projects = ref([
  // 1. LANDING PAGE
  {
     id: 'landing-page',
    title: 'Creative Landing Page',
    description: 'A high-converting landing page with modern animations, responsive layout, and SEO optimization designed to boost user engagement.',
    techStack: ['Vue.js', 'Tailwind CSS', 'AOS'],
    image: 'https://images.unsplash.com/photo-1633356122544-f134324a6cee?auto=format&fit=crop&w=1350&q=80',
    // Yahan Link Dalain
    link: 'https://your-landing-page-link.com' 
  },
  // 2. E-COMMERCE
  {
     id: 'ecommerce',
    title: 'E-commerce Platform',
    description: 'A full-featured e-commerce website built with Next.JS and React, featuring product filtering, cart functionality, and secure checkout.',
    techStack: ['Next.JS', 'React', 'CSS3'],
    image: 'ecom.png',
    // Yahan Link Dalain
    link: 'https://chrono-lux.odoo.com/'
  },
  // 3. DASHBOARD
  {
    id: 'dashboard',
    title: 'Analytics Dashboard',
    description: 'An interactive dashboard for data visualization with real-time updates, built with React and Chart.js.',
    techStack: ['React', 'Chart.js', 'Bootstrap'],
    image: 'https://images.unsplash.com/photo-1551288049-bebda4e38f71?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80',
    // Yahan Link Dalain
    link: 'https://your-dashboard-link.com'
  },
  // 4. CHROME EXTENSION
  {
     id: 'extension',
    title: 'Productivity Chrome Extension',
    description: 'A browser extension that helps users stay focused and manage their time effectively while browsing.',
    techStack: ['Chrome Extension', 'JavaScript'],
    image: 'https://images.unsplash.com/photo-1484480974693-6ca0a78fb36b?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80',
    // Yahan Link Dalain
    link: 'https://your-extension-link.com'
  }
]);

const swapColors = ref(false);
let intervalId = null;

onMounted(() => {
  intervalId = setInterval(() => {
    swapColors.value = !swapColors.value;
  }, 3000);
});

onUnmounted(() => {
  if (intervalId) clearInterval(intervalId);
});
</script>

<style scoped>
.custom-bounce { animation: jumpAndWait 3s infinite ease-in-out; }
@keyframes jumpAndWait {
  0%, 20%, 50%, 80%, 100% { transform: translateY(0); }
  10% { transform: translateY(-6px); } 
  30% { transform: translateY(-3px); }
}

.group\/btn:hover .animate-shine { animation: shineMove 0.7s forwards; }
@keyframes shineMove { 0% { left: -100%; } 100% { left: 200%; } }
</style>