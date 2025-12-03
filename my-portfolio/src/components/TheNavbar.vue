<template>
  <nav class="fixed top-0 left-0 w-full z-50 flex justify-between items-center py-4 px-6 md:px-12 bg-[#a2a7b0]/90 backdrop-blur-md shadow-sm transition-all duration-300 font-poppins">
    
    <!-- Logo Section -->
    <a href="" class="flex items-center gap-2 cursor-pointer select-none group">
      <div class="text-3xl font-bold tracking-tight font-poppins">
        <span class="text-brand-green">Wel</span>
        <span class="text-white">come</span>
        <span class="text-red-600 text-5xl inline-block dot-anim">.</span>
      </div>
    </a>

    <!-- Desktop Navigation -->
    <!-- Added 'items-center' to align button perfectly -->
    <ul class="hidden md:flex gap-8 text-white items-center">
      <li v-for="item in navItems" :key="item">
        <!-- CHANGE 1: 'text-sm' hata kar 'text-lg font-bold' kar diya -->
        <a :href="`#${item.toLowerCase()}`" 
           class="hover:text-brand-green transition-colors duration-300 relative group text-lg font-bold uppercase tracking-wider">
           {{ item }}
           <span class="absolute -bottom-1 left-0 w-0 h-0.5 bg-brand-green transition-all duration-300 group-hover:w-full"></span>
        </a>
      </li>

      <!-- CHANGE 2: Resume Button Added -->
      <li>
        <a href="/resume.pdf" download target="_blank" class="bg-brand-green text-white px-6 py-2 rounded-full text-lg font-bold shadow-md hover:bg-white hover:text-brand-green transition-all duration-300">
          Resume
        </a>
      </li>
    </ul>

    <!-- Mobile Menu Button -->
    <button @click="toggleMenu" class="md:hidden text-white text-3xl focus:outline-none z-50">
      {{ isMenuOpen ? '✕' : '☰' }}
    </button>

    <!-- Mobile Menu Overlay -->
    <div v-if="isMenuOpen" class="absolute top-0 left-0 w-full h-screen bg-[#a2a7b0] flex flex-col justify-center items-center shadow-xl md:hidden animate-fade-in-up">
      <ul class="flex flex-col gap-8 text-center items-center">
        <li v-for="item in navItems" :key="item">
          <a :href="`#${item.toLowerCase()}`" @click="toggleMenu" class="text-2xl font-bold text-white hover:text-brand-green transition-colors">
            {{ item }}
          </a>
        </li>
        
        <!-- Mobile Resume Button -->
        <li>
           <a href="/resume.pdf" download class="text-2xl font-bold text-brand-green border-2 border-brand-green px-6 py-2 rounded-full hover:bg-brand-green hover:text-white transition-all">
            Resume
          </a>
        </li>
      </ul>
    </div>

  </nav>
</template>

<script setup>
import { ref } from 'vue';
const navItems = ref(['Home', 'About', 'Projects', 'Services', 'Contact']);
const isMenuOpen = ref(false);
const toggleMenu = () => { isMenuOpen.value = !isMenuOpen.value; };
</script>

<style scoped>
.dot-anim { animation: gentleBounce 2s infinite ease-in-out; }
@keyframes gentleBounce { 0%, 100% { transform: translateY(0); } 50% { transform: translateY(-10px); } }
.animate-fade-in-up { animation: fadeIn 0.3s ease-out forwards; }
@keyframes fadeIn { from { opacity: 0; transform: translateY(-20px); } to { opacity: 1; transform: translateY(0); } }
</style>