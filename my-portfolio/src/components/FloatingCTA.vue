<template>
  <div class="fixed right-6 bottom-6 z-50">
    <button @click="$emit('openContact')" class="w-14 h-14 rounded-full flex items-center justify-center glass-card shadow-2xl transform hover:scale-105 transition">
      <div class="w-10 h-10 bg-gradient-to-tr from-pink-500 to-rose-400 rounded-full flex items-center justify-center text-white text-2xl font-bold">+</div>
    </button>
  </div>
</template>

<script>
export default {
  name: "FloatingCTA",
};
</script>

<style scoped>
/* nothing extra */
</style>
