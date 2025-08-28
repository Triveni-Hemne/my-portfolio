<template>
  <!-- Skills Grid -->
   
  <section id="skills" class="bg-sky-50 py-16 px-4 ">
    <div class="max-w-6xl mx-auto text-center ">
      <h2 class="text-3xl font-bold text-deepblue mb-6">Skills & Technologies</h2>

      <!-- Filter Buttons -->
      <div class="flex justify-center flex-wrap gap-4 mb-8">
        <button
          v-for="category in categories"
          :key="category"
          @click="selectedCategory = category"
          :class="[
            'px-4 py-2 rounded-full text-sm font-semibold transition',
            selectedCategory === category
              ? 'bg-sky-dark text-sky-300'
              : 'bg-white border border-sky-dark text-sky-dark hover:bg-sky-dark hover:text-sky-300 hover:cursor-pointer'
          ]"
        >
          {{ category }}
        </button>
      </div>

      <!-- Skills Grid -->
       <div class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 lg:grid-cols-6 gap-y-15 place-items-center">
        <Cube v-for="(skill, i) in filteredSkills" :key="i" :skill="skill" />
      </div> 

    </div>

  </section>
  
</template>

<script>
import Cube from "./Cube.vue";
export default {
  name: 'SkillsSection',
  components: { Cube },
  data() {
    return {
      selectedCategory: 'All',
      categories: ['All', 'Frontend', 'Backend', 'Tools', 'Programming Languages'],
      skills: [
        
        // Backend
        { name: 'Laravel', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/laravel/laravel-original.svg', category: 'Backend' },
        { name: 'MySQL', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/mysql/mysql-original.svg', category: 'Backend' },
        { name: 'PHP', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/php/php-original.svg', category: 'Backend' },

        // Tools
        { name: 'Git', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/git/git-original.svg', category: 'Tools' },
        { name: 'Linux', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/linux/linux-original.svg', category: 'Tools' },
        { name: 'Figma', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/figma/figma-original.svg', category: 'Tools' },

        // Programming Languages
        { name: 'C', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/c/c-original.svg', category: 'Programming Languages' },

        // Frontend
        { name: 'Vue.js', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/vuejs/vuejs-original.svg', category: 'Frontend' },
        { name: 'JavaScript', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/javascript/javascript-original.svg', category: 'Frontend' },
        { name: 'Tailwind', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/tailwindcss/tailwindcss-original.svg', category: 'Frontend' },
        { name: 'Bootstrap', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/bootstrap/bootstrap-original.svg', category: 'Frontend' },
        { name: 'CSS', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/css3/css3-original.svg', category: 'Frontend' },
        { name: 'HTML', icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/html5/html5-original.svg', category: 'Frontend' },
      ]
    };
  },
  computed: {
    filteredSkills() {
      if (this.selectedCategory === 'All') {
        return this.skills;
      }
      return this.skills.filter(skill => skill.category === this.selectedCategory);
    },
  }
};
</script>

