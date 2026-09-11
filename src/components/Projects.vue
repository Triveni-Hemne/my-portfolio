<template>
  <section id="projects" class="bg-slate-50 py-16 px-4">
    <div class="max-w-7xl mx-auto">
      <h2 class="text-3xl font-bold text-slate-800 text-center mb-10">My Projects</h2>

      <div class="grid gap-8 sm:grid-cols-2 lg:grid-cols-3">
        <div
          v-for="(project, index) in projects"
          :key="index"
          class="bg-white rounded-2xl shadow-md overflow-hidden border hover:shadow-lg transition"
        >
          <img
            :src="project.image"
            alt="Project Screenshot"
            class="w-full h-40 object-cover"
          />
          <div class="p-5">
            <h3 class="text-xl font-semibold text-slate-800 mb-2">{{ project.title }}</h3>
            <p class="text-slate-600 text-sm mb-4">{{ project.description }}</p>
            <p class="text-sm italic text-gray-500 border-l-4 border-yellow-400 pl-3 mb-3">{{ project.note }}</p>
            <div class="flex gap-3">
              <a
                v-if="project.demo"
                :href="project.demo"
                target="_blank"
                class="text-cyan-600 text-sm font-medium hover:underline"
              >Live Demo</a>
              <a
                v-if="project.github"
                :href="project.github"
                target="_blank"
                class="text-slate-600 text-sm font-medium hover:underline"
              >GitHub</a>
            </div>
          </div>
        </div>
      </div>
    </div>

    
  </section>
</template>

<script>
import img0 from '@/assets/images/project-mini-bank.png'
import img1 from '@/assets/images/project-cooperative-society.png'
import img2 from '@/assets/images/project-it-online-examination.png'
import img3 from '@/assets/images/project-portfolio-site.png'
export default {
  name: 'Projects',
  data() {
    return {
      projects: [
        {
          title: "Mini Bank System",
          description: "A modern full-stack banking application built using Laravel, Vue 3, and Inertia.js. It includes account management, transactions, dashboards, and financial reporting.",
          image: img0,
          github: "https://github.com/Triveni-Hemne/mini-bank", // Not public
          demo: "",   // Not public
          note: "Personal project built to practice real-world banking system architecture and modern full-stack development."
        },
        {
          title: "Cooperative Society Management System",
          description: "A full-stack internal tool built with Laravel to manage member accounts, daily transactions, financial reports, passbooks, and administrative controls.",
          image: img1,
          github: "", // Not public
          demo: "",   // Not public
          note: "Developed as part of my role at RTSoft Solutions. Code and demo are not publicly available due to company confidentiality."
        },
        {
          title: "IT Online Examination System",
          description: "A Laravel-based backend system that enables IT students to participate in online exams, with features like question banks, scoring logic, and result tracking.",
          image: img2,
          github: "", // Not public
          demo: "",   // Not public
          note: "Developed as part of my role at RTSoft Solutions. Code and demo are not publicly available due to company confidentiality."
        },
        {
          title: "Freelance / Client Projects",
          description: "Worked on real-world production applications involving UI improvements, bug fixing, content updates, and deployment support.",
          image: img1,
          github: "", // Not public
          demo: "",   // Not public
          note: "Includes multiple client projects. Links are not public due to client privacy."
        },
        {
          title: "Portfolio Website",
          description: "A personal portfolio built using Vue.js and Tailwind CSS, showcasing selected projects, work experience, and contact information.",
          image: img3,
          github: "https://github.com/Triveni-Hemne/my-portfolio",
          demo: "https://triveni-hemne.github.io/my-portfolio/", // Replace with actual portfolio site URL when ready
          note: "Live demo available. Source code can be shared upon request."
        },
      ]
    };
  }
};
</script>
