<template>
  <section id="home" class="pt-24 pb-16 bg-slate-50">
    <div class="max-w-7xl mx-auto px-4 flex flex-col-reverse md:flex-row items-center gap-8">
      
      <!-- Text Content -->
      <div class="flex-1 text-center md:text-left">
        <h1 class="text-4xl md:text-5xl font-bold text-slate-800 mb-4">
          Hi, I'm <span class="text-cyan-600">Triveni Hemne</span>
        </h1>
        <p class="text-lg text-slate-600 mb-6">
          A passionate Software Engineer building modern web apps with Laravel and Vue.js.
        </p>
        <div class="flex justify-center md:justify-start gap-4">
          <a href="#projects">
           <BaseButton variant="see-my-work">See My Work</BaseButton>
          </a>
          <a href="#contact" >
            <BaseButton variant="outline">Contact Me</BaseButton>
          </a>
        </div>
      </div>

      <!-- Image or Illustration -->
      <div class="flex-1">
        <img
          :src="('../assets/images/hero-developer-illustration.png')"
          alt="Developer Illustration"
          class="w-full max-w-sm mx-auto"
        />
      </div>
    </div>
  </section>
</template>

<script>
import BaseButton from './Button.vue';
export default {
  components: {
    BaseButton
  }
}
</script>
