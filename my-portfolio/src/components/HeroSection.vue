<template>
  <!-- ID="home" mojood hai, Nav link ab kaam karega -->
  <section id="home"
    class="min-h-screen flex flex-col md:flex-row items-center justify-between px-6 md:px-12 pt-20 font-poppins overflow-hidden"
    style="background: linear-gradient(105deg, #a2a7b0 0%, #a2a7b0 50%, #bbf7d0 40%, #4ade80 100%);"
  >
    
   
    <div class="flex-1 md:pr-4 z-10 animate-fade-in-up mt-10 md:-mt-24  flex flex-col justify-center items-centerstart text-center md:text-left">
      <h1 class="text-5xl md:text-6xl font-bold text-white leading-tight mb-2">
        Hi, I'm <span class="text-brand-green bg-white/10 px-2 rounded-lg">Zubair Khan</span>
      </h1>
      <h2 class="text-3xl md:text-4xl font-extrabold text-white mb-4">
        Front End Developer
      </h2>
      <p class="text-gray-100 text-base max-w-md mb-6 leading-relaxed">
        Building responsive and beautiful web experiences using Vue.js and Tailwind CSS.
      </p>
      
      <div class="flex items-center">
        <!-- CHANGE: Button ko 'a' tag bana diya aur href="#projects" laga diya -->
        <a href="#projects" class="custom-bounce relative overflow-hidden group bg-brand-green text-white px-8 py-3 rounded-full font-semibold text-lg shadow-lg shadow-green-900/50 hover:shadow-green-400 transition-all duration-300 whitespace-nowrap inline-block cursor-pointer  mb-12">
          <span class="relative z-10">View My Work</span>
          <div class="absolute top-0 -left-[100%] w-full h-full bg-gradient-to-r from-transparent via-white/40 to-transparent -skew-x-12 group-hover:animate-shine"></div>
        </a>
      </div>
    </div>

    <!-- Right Side: Image Section -->
    <div class="flex-1 flex justify-center md:justify-end items-center relative mt-12 md:mt-0 md:pl-10 animate-slide-in-right">
      
      <div class="absolute right-10 w-[300px] h-[300px] bg-white opacity-20 rounded-full blur-3xl -z-10"></div>
      
      <!-- Main Circle Container -->
      <!-- Change 2: '-translate' wali classes ke sath 'md:' lagaya hai taake mobile par image upar na charhay -->
      <!-- Change 3: Width/Height ko fix kiya hai (Mobile: w-64, Desktop: w-[450px]) -->
      <div class="relative w-64 h-64 md:w-[350px] md:h-[350px] flex justify-center rounded-full border-[6px] border-white/50 p-2 shadow-2xl bg-white/10 backdrop-blur-sm md:-translate-y-16 md:-translate-x-16">
        
        <div class="w-full h-full rounded-full overflow-hidden border-2 border-white/30 relative">
          <img 
            :src="myProfileImage" 
            alt="Zubair Khan" 
            class="w-full h-full object-cover object-[50%_13%] hover:scale-105 transition-transform duration-500"
          />
        </div>

      </div>
         </div>
  </section>
</template>

<script setup>
import myProfileImage from '../assets/portfolio.jpg' 
</script>

<style scoped>
.custom-bounce { animation: jumpAndWait 3s infinite ease-in-out; }
@keyframes jumpAndWait {
  0%, 20%, 50%, 80%, 100% { transform: translateY(0); }
  10% { transform: translateY(-10px); }
  30% { transform: translateY(-5px); }
}
.group:hover .animate-shine { animation: shineMove 0.7s forwards; }
@keyframes shineMove { 0% { left: -100%; } 100% { left: 200%; } }
</style>