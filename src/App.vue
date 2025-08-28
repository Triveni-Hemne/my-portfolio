<template>
 <div class="">
    <Header />
    <HeroSection />
    <AboutMe />
    <Skills/>
    <Experience/>
    <Projects />
    <ContactFrom />
    <Footer />
  </div>
</template>

<script>
import "tailwindcss";
import { defineComponent } from 'vue'
import HeroSection from './components/HeroSection.vue'
import Header from './components/Header.vue'
import AboutMe from './components/AboutMe.vue'
import Skills from './components/Skills.vue'
import Experience from './components/Experience.vue'
import Projects from './components/Projects.vue'
import ContactFrom from './components/ContactForm.vue'
import Footer from './components/Footer.vue'

export default defineComponent({
  components: { 
    HeroSection,
    Header,
    AboutMe,
    Skills,
    Experience,
    Projects,
    ContactFrom,
    Footer,
   },
    setup() {
        
    },

    name:"App"
})
</script>

<style scoped>

</style>
