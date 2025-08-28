<template>
  <header class="bg-white shadow-md fixed top-0 left-0 w-full z-50">
    <nav class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 flex justify-between items-center h-16">
      <!-- Logo / Name -->
      <div class="text-xl font-bold text-cyan-600">
        Triveni.dev
      </div>

      <!-- Navigation Links -->
      <ul class="hidden md:flex space-x-6 text-slate-800 font-medium">
        <li v-for="link in links" :key="link.id">
          <a :href="`#${link.id}`"
             :class="activeSection === link.id ? 'text-cyan-600 font-semibold border-b-2 border-cyan-600' : 'hover:text-cyan-500'"
             class="transition">
            {{ link.label }}
          </a>
        </li>
      </ul>

      <!-- Mobile Menu Button -->
      <button @click="toggleMenu" class="md:hidden text-slate-800 focus:outline-none">
        <svg v-if="!menuOpen" xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none"
             viewBox="0 0 24 24" stroke="currentColor">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                d="M4 6h16M4 12h16M4 18h16"/>
        </svg>
        <svg v-else xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none"
             viewBox="0 0 24 24" stroke="currentColor">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                d="M6 18L18 6M6 6l12 12"/>
        </svg>
      </button>
    </nav>

    <!-- Mobile Menu -->
    <div v-if="menuOpen" class="md:hidden bg-white shadow-md px-4 pb-4">
      <ul class="flex flex-col space-y-2 text-slate-800 font-medium">
        <li><a @click="toggleMenu" href="#home">Home</a></li>
        <li><a @click="toggleMenu" href="#about">About</a></li>
        <li><a @click="toggleMenu" href="#skills">Skills</a></li>
        <li><a @click="toggleMenu" href="#experience">Experience</a></li>
        <li><a @click="toggleMenu" href="#projects">Projects</a></li>
        <li><a @click="toggleMenu" href="#contact">Contact</a></li>
      </ul>
    </div>
  </header>
</template>

<script>
export default {
  name: 'Header',
  data() {
    return {
      menuOpen: false,
      activeSection: 'home',
      links: [
        { id: 'home', label: 'Home' },
        { id: 'about', label: 'About' },
        { id: 'skills', label: 'Skills' },
        { id: 'experience', label: 'Experience' },
        { id: 'projects', label: 'Projects' },
        { id: 'contact', label: 'Contact' }
      ]
    }
  },
  methods: {
    toggleMenu() {
      this.menuOpen = !this.menuOpen
    },
    onScroll() {
      const sections = this.links.map(link => document.getElementById(link.id))
      const scrollY = window.scrollY + 100 // offset for header height

      for (let section of sections) {
        if (section && scrollY >= section.offsetTop && scrollY < section.offsetTop + section.offsetHeight) {
          this.activeSection = section.id
          break
        }
      }
    }
  },
  mounted() {
    window.addEventListener('scroll', this.onScroll)
  },
  beforeUnmount() {
    window.removeEventListener('scroll', this.onScroll)
  }
}
</script>
