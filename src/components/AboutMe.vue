<template>
  <section id="about" class="bg-white py-16 px-4">
    <div class="max-w-5xl mx-auto flex flex-col md:flex-row items-center gap-10">

      <!-- Image or Avatar -->
      <div class="w-40 h-40 rounded-full overflow-hidden border-4 border-cyan-600 shadow-md">
        <img
          :src="('../assets/images/profile.png')"
          alt="Your Profile"
          class="w-full h-full object-cover"
        />
      </div>

      <!-- About Text -->
      <div class="flex-1 text-center md:text-left">
        <h2 class="text-3xl font-bold text-slate-800 mb-4">
          About Me
        </h2>
        <p class="text-slate-600 text-lg leading-relaxed">
          I'm a <span class="font-medium text-cyan-600">Software Engineer</span> with 3+ years of experience crafting modern web applications using
          <strong class="text-cyan-600"> Laravel </strong> and
          <strong class="text-cyan-600"> Vue.js</strong>. Passionate about clean code, UI/UX, and solving real-world problems with elegant web solutions.
        </p>
        <p class="mt-4 text-slate-600">
          Currently working at <span class="font-semibold">RTSoft Solutions, Gondia</span>, I also train aspiring developers and contribute to open source.
        </p>
     <!-- Resume Download Button -->
      <ResumeBtn />

      </div>

    </div>
  </section>
</template>

<script>
import ResumeBtn from './ResumeDownload.vue'

export default {
  name: 'AboutMe',
  components: { 
    ResumeBtn,
   }
}
</script>
