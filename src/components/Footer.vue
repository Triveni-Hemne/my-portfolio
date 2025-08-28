<template>
  <footer class="bg-slate-800 text-white py-8 mt-16">
    <div class="max-w-7xl mx-auto px-4 flex flex-col md:flex-row justify-between items-center gap-4">

      <!-- Left: Logo or Name -->
      <div class="text-center md:text-left text-lg font-semibold mx-auto">
        © {{ new Date().getFullYear() }} Triveni Hemne. All rights reserved.
      </div>

      <!-- Right: Social Links -->
      <div class="flex gap-4">
        <a href="https://github.com/yourgithub" target="_blank" class="hover:text-sky-400">
          <i class="fab fa-github text-xl"></i>
        </a>
        <a href="https://linkedin.com/in/yourlinkedin" target="_blank" class="hover:text-sky-400">
          <i class="fab fa-linkedin text-xl"></i>
        </a>
        <a href="mailto:you@example.com" class="hover:text-sky-400">
          <i class="fas fa-envelope text-xl"></i>
        </a>
      </div>

    </div>
  </footer>
</template>

<script>
export default {
  name: 'FooterSection'
}
</script>
