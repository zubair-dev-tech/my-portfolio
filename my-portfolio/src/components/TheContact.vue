<template>
  <section id="contact" class="bg-[#9ca3af] py-20 px-6 md:px-12 relative">
    <div class="max-w-7xl mx-auto">
      
      <!-- TITLE SECTION -->
      <div class="text-center mb-16">
        <h2 class="text-5xl font-extrabold tracking-wide transition-colors duration-500" :class="isGreen ? 'text-green-400' : 'text-white'">
          Contact Me
        </h2>
        <div class="h-2 w-24 mx-auto mt-4 rounded-full transition-colors duration-500" :class="isGreen ? 'bg-green-400' : 'bg-white'"></div>
        <p class="text-gray-100 mt-6 text-lg font-medium">Get in touch to discuss your project or just say hello</p>
      </div>

      <div class="grid grid-cols-1 lg:grid-cols-2 gap-16 items-start">
        
        <!-- LEFT SIDE: INFO -->
        <div class="space-y-10 mt-4">
          <div class="group flex items-center space-x-6 p-6 rounded-2xl transition-all duration-300 hover:bg-green-500 cursor-pointer bg-white/5 border border-white/10 hover:shadow-xl hover:-translate-y-1">
            <div class="flex-shrink-0 bg-green-100 p-4 rounded-full text-green-500 group-hover:bg-white group-hover:text-green-600 transition-colors">
              <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" class="w-8 h-8"><path stroke-linecap="round" stroke-linejoin="round" d="M15 10.5a3 3 0 11-6 0 3 3 0 016 0z" /><path stroke-linecap="round" stroke-linejoin="round" d="M19.5 10.5c0 7.142-7.5 11.25-7.5 11.25S4.5 17.642 4.5 10.5a7.5 7.5 0 1115 0z" /></svg>
            </div>
            <div>
              <h3 class="text-2xl font-bold text-gray-800 group-hover:text-white transition-colors">Location</h3>
              <p class="text-gray-200 text-lg group-hover:text-white transition-colors">Lahore, Pakistan</p>
            </div>
          </div>
          
          <div class="group flex items-center space-x-6 p-6 rounded-2xl transition-all duration-300 hover:bg-green-500 cursor-pointer bg-white/5 border border-white/10 hover:shadow-xl hover:-translate-y-1">
            <div class="flex-shrink-0 bg-green-100 p-4 rounded-full text-green-500 group-hover:bg-white group-hover:text-green-600 transition-colors">
              <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" class="w-8 h-8"><path stroke-linecap="round" stroke-linejoin="round" d="M21.75 6.75v10.5a2.25 2.25 0 01-2.25 2.25h-15a2.25 2.25 0 01-2.25-2.25V6.75m19.5 0A2.25 2.25 0 0019.5 4.5h-15a2.25 2.25 0 00-2.25 2.25m19.5 0v.243a2.25 2.25 0 01-1.07 1.916l-7.5 4.615a2.25 2.25 0 01-2.36 0L3.32 8.91a2.25 2.25 0 01-1.07-1.916V6.75" /></svg>
            </div>
            <div>
              <h3 class="text-2xl font-bold text-gray-800 group-hover:text-white transition-colors">Email</h3>
              <p class="text-gray-200 text-lg group-hover:text-white transition-colors">zubairdev00@gmail.com</p>
            </div>
          </div>

          <div class="group flex items-center space-x-6 p-6 rounded-2xl transition-all duration-300 hover:bg-green-500 cursor-pointer bg-white/5 border border-white/10 hover:shadow-xl hover:-translate-y-1">
            <div class="flex-shrink-0 bg-green-100 p-4 rounded-full text-green-500 group-hover:bg-white group-hover:text-green-600 transition-colors">
              <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" class="w-8 h-8"><path stroke-linecap="round" stroke-linejoin="round" d="M2.25 6.75c0 8.284 6.716 15 15 15h2.25a2.25 2.25 0 002.25-2.25v-1.372c0-.516-.351-.966-.852-1.091l-4.423-1.106c-.44-.11-.902.055-1.173.417l-.97 1.293c-.282.376-.769.542-1.21.38a12.035 12.035 0 01-7.143-7.143c-.162-.441.004-.928.38-1.21l1.293-.97c.363-.271.527-.734.417-1.173L6.963 3.102a1.125 1.125 0 00-1.091-.852H4.5A2.25 2.25 0 002.25 4.5v2.25z" /></svg>
            </div>
            <div>
              <h3 class="text-2xl font-bold text-gray-800 group-hover:text-white transition-colors">Phone</h3>
              <p class="text-gray-200 text-lg group-hover:text-white transition-colors">+92 325 3214 336</p>
            </div>
          </div>
        </div>

        <!-- RIGHT SIDE: FORM -->
        <form @submit.prevent="sendEmail" class="space-y-6 bg-white/5 p-8 rounded-3xl border border-white/10 shadow-lg">
          
          <!-- Inputs (Same as before) -->
          <div>
            <input v-model="form.name" type="text" placeholder="Your Name" :class="{'ring-2 ring-red-500': errors.name}" class="w-full px-6 py-4 text-lg rounded-xl bg-white border-none shadow-md text-gray-700 placeholder-gray-400 focus:outline-none focus:ring-2 focus:ring-green-400 transition-all">
            <p v-if="errors.name" class="text-red-500 text-sm mt-1 ml-2">Name is required</p>
          </div>

          <div>
            <input v-model="form.email" type="email" placeholder="Your Email" :class="{'ring-2 ring-red-500': errors.email}" class="w-full px-6 py-4 text-lg rounded-xl bg-white border-none shadow-md text-gray-700 placeholder-gray-400 focus:outline-none focus:ring-2 focus:ring-green-400 transition-all">
            <p v-if="errors.email" class="text-red-500 text-sm mt-1 ml-2">Email is required</p>
          </div>

          <div>
            <input v-model="form.subject" type="text" placeholder="Subject" :class="{'ring-2 ring-red-500': errors.subject}" class="w-full px-6 py-4 text-lg rounded-xl bg-white border-none shadow-md text-gray-700 placeholder-gray-400 focus:outline-none focus:ring-2 focus:ring-green-400 transition-all">
            <p v-if="errors.subject" class="text-red-500 text-sm mt-1 ml-2">Subject is required</p>
          </div>

          <div>
            <textarea v-model="form.message" rows="5" placeholder="Your Message" :class="{'ring-2 ring-red-500': errors.message}" class="w-full px-6 py-4 text-lg rounded-xl bg-white border-none shadow-md text-gray-700 placeholder-gray-400 focus:outline-none focus:ring-2 focus:ring-green-400 resize-none transition-all"></textarea>
            <p v-if="errors.message" class="text-red-500 text-sm mt-1 ml-2">Message cannot be empty</p>
          </div>

          <!-- Button (Loading State Added) -->
          <div class="text-left pt-2">
            <button 
              type="submit" 
              :disabled="isLoading"
              class="w-full sm:w-auto bg-green-500 hover:bg-green-600 text-white font-bold text-xl py-4 px-12 rounded-full transition duration-300 shadow-xl hover:shadow-2xl transform hover:-translate-y-1 disabled:bg-gray-400 disabled:cursor-not-allowed"
            >
              {{ isLoading ? 'Sending...' : 'Send Message' }}
            </button>
          </div>
        </form>

      </div>
    </div>

    <!-- SUCCESS POPUP -->
    <div v-if="showModal" class="fixed inset-0 flex items-center justify-center z-50 bg-black/60 backdrop-blur-sm">
      <div class="bg-white rounded-3xl p-8 md:p-12 shadow-2xl max-w-md w-full text-center">
        <div class="w-24 h-24 bg-green-100 rounded-full flex items-center justify-center mx-auto mb-6">
          <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" class="w-12 h-12 text-green-600"><path stroke-linecap="round" stroke-linejoin="round" d="M4.5 12.75l6 6 9-13.5" /></svg>
        </div>
        <h3 class="text-3xl font-extrabold text-gray-800 mb-2">Thank You!</h3>
        <p class="text-gray-500 text-lg mb-8">Thanks for contacting me, <strong>{{ form.name }}</strong>. <br> I will reply to you shortly!</p>
        <button @click="closeModal" class="w-full bg-green-500 hover:bg-green-600 text-white font-bold py-3 px-6 rounded-xl transition duration-300 shadow-md">Close</button>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, reactive, onMounted, onUnmounted } from 'vue';
// EmailJS Import zaroori hai
import emailjs from '@emailjs/browser';

// --- Animation Logic ---
const isGreen = ref(false);
let intervalId = null;
onMounted(() => {
  intervalId = setInterval(() => { isGreen.value = !isGreen.value; }, 2000);
});
onUnmounted(() => { if (intervalId) clearInterval(intervalId); });

// --- Form Logic ---
const showModal = ref(false);
const isLoading = ref(false);
const form = reactive({ name: '', email: '', subject: '', message: '' });
const errors = reactive({ name: false, email: false, subject: false, message: false });

const sendEmail = () => {
  // 1. Validation
  errors.name = !form.name;
  errors.email = !form.email;
  errors.subject = !form.subject;
  errors.message = !form.message;

  if (!errors.name && !errors.email && !errors.subject && !errors.message) {
    
    // 2. Loading Start
    isLoading.value = true;

    // ============================================================
    // YAHAN APNI ASLI IDS PASTE KAREIN (Quotes '' k andar)
    // ============================================================
    const serviceID = 'service_nnhi5sq';   // e.g. 'service_xyz'
    const templateID = 'template_bpigy7n'; // e.g. 'template_abc'
    const publicKey = 'ct77-42bByIbl2qud';   // e.g. 'user_123456'
    // ============================================================

    const templateParams = {
      name: form.name,
      email: form.email,
      subject: form.subject,
      message: form.message
    };

    emailjs.send(serviceID, templateID, templateParams, publicKey)
      .then((response) => {
        console.log('SUCCESS!', response.status, response.text);
        isLoading.value = false;
        showModal.value = true; // Popup Show hoga
      }, (err) => {
        console.log('FAILED...', err);
        isLoading.value = false;
        // Agar ab bhi error aye to console check karen
        alert("Error: " + JSON.stringify(err)); 
      });
  }
};

const closeModal = () => {
  showModal.value = false;
  form.name = '';
  form.email = '';
  form.subject = '';
  form.message = '';
};
</script>