<template>
  <!-- 
    CHANGES:
    1. Removed style="background: linear-gradient..."
    2. Added class="bg-[#a2a7b0]" (Ye wahi grey color hai).
    Ab ye color puri website k peeche hoga.
  -->
  <div class="min-h-screen w-full bg-[#a2a7b0]">
    
    <TheNavbar />
    <!-- Hero Section ab apna background khud sambhalega -->
    <HeroSection />
    <TheAbout />
    <TheProjects />
    <TheServices />
    <TheContact />
    <TheFooter />
  </div>
</template>

<script setup>
import TheNavbar from './components/TheNavbar.vue';
import HeroSection from './components/HeroSection.vue';
import TheAbout from './components/TheAbout.vue';
import TheProjects from './components/TheProjects.vue';
import TheServices from './components/TheServices.vue';
import TheContact from './components/TheContact.vue';
import TheFooter from './components/TheFooter.vue';
</script>

<style>
html { scroll-behavior: smooth; }
</style>