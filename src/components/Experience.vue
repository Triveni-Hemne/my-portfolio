<template>
  <section id="experience" class="bg-white py-16 px-4">
    <div class="max-w-5xl mx-auto">
      <h2 class="text-3xl font-bold text-deepblue text-center mb-10">Experience</h2>
    <div class="text-center mb-12">
        <h3 class="text-2xl font-semibold text-deepblue">
          {{ experiences[0].role }}
        </h3>
        <p class="text-lg text-sky-dark">@ {{ experiences[0].company }}</p>
      </div>
      <div class="relative border-l-4 border-sky-dark pl-6 space-y-10">

        <div 
          v-for="(exp, index) in experiences[0].details" 
          :key="index" 
          class="relative group flex items-center gap-8"
          :class="index % 2 === 0 ? 'flex-row' : 'flex-row-reverse'"
        >
          <!-- Dot -->
          <span class="absolute -left-[20px] top-6 w-4 h-4 rounded-full bg-sky-dark border-5 border-sky-500"></span>

          <!-- Image -->
          <div class="w-1/4">
            <img :src="exp.image" alt="experience image" class="rounded-lg shadow-lg" />
          </div>

          <!-- Content -->
          <div class="w-2/3">
            <h4 class="font-semibold text-sky-dark text-lg mb-1">
              {{ exp.heading }}
            </h4>
            <!-- Toggle Button (only on mobile) -->
            <button 
              @click="togglePoints(index)"
              class="md:hidden text-cyan-600 font-medium mb-2"
            >
              {{ showPoints === index ? 'Hide Details' : 'Show Details' }}
            </button>
            <!-- Points List -->
            <transition
              enter-active-class="transition-all duration-500 ease-in-out"
              leave-active-class="transition-all duration-500 ease-in-out"
              enter-from-class="max-h-0 opacity-0"
              enter-to-class="max-h-screen opacity-100"
              leave-from-class="max-h-screen opacity-100"
              leave-to-class="max-h-0 opacity-0"
            >
            <ul v-show="isDesktop || openIndex === index"
              class="list-disc list-inside text-slate-700 space-y-1 pl-4 overflow-hidden"
            >
              <li v-for="(point, pIndex) in exp.points" :key="pIndex">
                {{ point }}
              </li>
            </ul>
            </transition>
          </div>
        </div>

      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'ExperienceSection',
  props: ['exp'], 
  data() {
    return {
      experiences: [
        {
          role: "Software Engineer & Trainer",
          company: "RTSoft Solutions LLP, Gondia",
          period: "2022 – Present",
          website: "https://rtsoftsolutions.com", // optional
          logo: "rtsoft-logo.png", // optional for UI
          details: [
            {
              heading:"📅 2025 – Enterprise App Development",
              points:[
                "🏛️ Cooperative Society Bank Management System – Full-stack Laravel + MySQL system.",
                "Core Modules: Loan, Deposits, Shares, Passbooks, Reports, Vouchers.",
                "Integrated cPanel deployments, role-based access control.",
                "Assisted in real-time invigilation and technical support for 12th-grade IT practical exams at local schools.",
                "Developed Vue.js personal portfolio from scratch.",
                "Incorporated AI-assisted development practices to enhance productivity and explore alternate solutions."
              ],
              image: "../assets/images/experience-image1.webp"
            },
              {
                heading:"📅 2024 – Real-World Project Exposure",
                points:[
                  "🍽️ Food Ordering/Mess Mgmt. – Created Laravel backend & Bootstrap UI.",
                  "👨‍💻 Online Examination System – Admin panel with Laravel.",
                  "Continued new-batch training cycles on HTML, CSS, and JS basics.",
                ],
                image:"../assets/images/experience-image2.webp"
              },
    
                {
                  heading: "📅 2023 – Tech Stack & Practice Projects",
                  points:[
                    "Multiple batches on HTML, SCSS, MySQL, and Bootstrap.",
                    "Conducted Linux basics & SQL query-building classes.",
                    "Git and GitHub practices introduced in training workflow.",
                  ],
                  image:"../assets/images/experience-image3.webp"
                },
                    {
                heading:"👨‍🏫 Training & Mentorship",
                points: [
                  "Conducted over 10+ training batches on MySQL, HTML, Figma and CSS.",
                  "Mentored 70+ students in web development; enabled them to confidently create functional websites.",
                  "Created structured notes, tutorials, and practical projects for learners."
                    ],
                    image:"../assets/images/experience-image4.webp"
                  },
                  
                  {
                    heading:"📅 2022 – Foundation Year",
                    points:[
                    "Jan–Mar: Introduced basic frontend technologies (HTML, CSS, JS).",
                    "Apr–May: Attempted to deliver MHCIT Certification Program; learned valuable lessons in planning and training delivery.",
                    "Jun: Developed 'Student Management System' using PHP & MySQL.",
                    "Jul–Sep: Focused on UI/UX using Figma and responsive design.",
                    "Oct–Dec: Delivered modules on Office Tools, C, C++, Computer Fundamentals.",
                    ],
                    image:"../assets/images/experience-image5.webp"
                  },
          ],
          techStack: [
            "PHP", "Laravel", "MySQL", "Vue.js", "Tailwind CSS", "Bootstrap", "Git", "cPanel", "Figma"
          ]
        },
      ],
      openIndex: null,                 // which item is open on mobile
      isDesktop: typeof window !== 'undefined' ? window.innerWidth >= 768 : true 
    };
  },
  methods: {
    togglePoints(i) {
      this.openIndex = (this.openIndex === i) ? null : i; // accordion behavior
    },
    handleResize() {
      this.isDesktop = window.innerWidth >= 768;
    }
  },
  mounted() {
    window.addEventListener('resize', this.handleResize);
  },
  beforeUnmount() {
    window.removeEventListener('resize', this.handleResize);
  }
  
};
</script>
