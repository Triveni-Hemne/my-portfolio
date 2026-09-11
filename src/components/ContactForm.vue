<template>
<section id="contact" class="py-20 px-4 bg-blue-50">
  <div class="max-w-6xl mx-auto flex flex-col md:flex-row items-center gap-12">

    <!-- LEFT: Illustration -->
    <div class="w-full md:w-1/2 flex justify-center">
      <img 
        :src="contactIllustration" 
        alt="Contact Illustration"
        class="max-w-sm md:max-w-md rounded-2xl shadow-lg"
      />
    </div>

    <!-- RIGHT: Content -->
    <div class="w-full md:w-1/2 text-center md:text-left">
      <h2 class="text-4xl font-bold text-slate-800 mb-4">Let’s Connect</h2>

      <p class="text-slate-600 mb-8">
        I’m always open to new opportunities, collaborations, or just a tech discussion.
        Feel free to reach out 👇
      </p>

      <!-- Email Card -->
      <a 
        href="mailto:trivenihemne1999@gmail.com"
        class="flex items-center gap-4 bg-white p-4 rounded-xl shadow hover:shadow-md transition mb-6 justify-center md:justify-start"
      >
        <span class="text-2xl">📧</span>
        <span class="text-slate-700 font-medium">trivenihemne1999@gmail.com</span>
      </a>

      <!-- Social Links -->
      <div class="flex gap-6 justify-center md:justify-start">

        <!-- GitHub -->
        <a 
          href="https://github.com/Triveni-Hemne"
          target="_blank"
          class="flex items-center gap-2 bg-slate-800 text-white px-5 py-3 rounded-full hover:bg-slate-900 transition shadow"
        >
          <!-- GitHub SVG -->
          <svg xmlns="http://www.w3.org/2000/svg" class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24">
            <path d="M12 .5C5.65.5.5 5.65.5 12a11.5 11.5 0 008 10.95c.6.1.82-.26.82-.58v-2.23c-3.25.7-3.94-1.56-3.94-1.56-.53-1.34-1.3-1.7-1.3-1.7-1.06-.73.08-.72.08-.72 1.17.08 1.78 1.2 1.78 1.2 1.04 1.78 2.73 1.27 3.4.97.1-.75.4-1.27.73-1.56-2.6-.3-5.33-1.3-5.33-5.8 0-1.28.46-2.33 1.2-3.15-.12-.3-.52-1.5.1-3.12 0 0 .98-.31 3.2 1.2a11.1 11.1 0 015.82 0c2.22-1.5 3.2-1.2 3.2-1.2.62 1.62.22 2.82.1 3.12.74.82 1.2 1.87 1.2 3.15 0 4.52-2.73 5.5-5.34 5.8.42.36.8 1.08.8 2.18v3.24c0 .32.22.68.83.58A11.5 11.5 0 0023.5 12C23.5 5.65 18.35.5 12 .5z"/>
          </svg>
          GitHub
        </a>

        <!-- LinkedIn -->
        <a 
          href="https://www.linkedin.com/in/triveni-hemne-6a30b1211"
          target="_blank"
          class="flex items-center gap-2 bg-blue-600 text-white px-5 py-3 rounded-full hover:bg-blue-700 transition shadow"
        >
          <!-- LinkedIn SVG -->
          <svg xmlns="http://www.w3.org/2000/svg" class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24">
            <path d="M20.45 20.45h-3.56v-5.57c0-1.33-.02-3.05-1.86-3.05-1.87 0-2.15 1.46-2.15 2.96v5.66H9.33V9h3.42v1.56h.05c.48-.9 1.65-1.86 3.4-1.86 3.63 0 4.3 2.39 4.3 5.49v6.26zM5.34 7.43a2.06 2.06 0 110-4.12 2.06 2.06 0 010 4.12zM7.12 20.45H3.56V9h3.56v11.45zM22.22 0H1.78C.8 0 0 .77 0 1.72v20.56C0 23.23.8 24 1.78 24h20.44c.98 0 1.78-.77 1.78-1.72V1.72C24 .77 23.2 0 22.22 0z"/>
          </svg>
          LinkedIn
        </a>

      </div>

      <!-- CTA -->
      <a 
        href="mailto:trivenihemne1999@gmail.com"
        class="inline-block mt-8 px-6 py-3 rounded-full shadow bg-cyan-600 text-white hover:bg-cyan-700 transition"
      >
        🚀 Hire Me
      </a>

    </div>

  </div>
</section>
</template>
<script>
import contactIllustration from '@/assets/images/side-illustration-contact.png'

export default {
  name: 'ContactSection',
  data() {
    return {
      contactIllustration
    }
  }
}
</script>