<template>
<section id="contact" class="py-20 px-4">
<div class="flex justify-center">

  <div class="max-w-100 hidden md:block">
     <img :src="('../assets/images/side-illustration-contact.png')" alt="dshfslfkj" class="rounded-tl-2xl rounded-bl-2xl">
  </div>
    <div class="max-w-2xl  text-center bg-blue-50 rounded-tr-2xl rounded-br-2xl rounded-bl-2xl md:rounded-bl-none md:rounded-tl-none rounded-tl-2xl px-15 py-5" >
      <h2 class="text-4xl font-bold text-slate-800 mb-4">Let’s Connect</h2>
      <p class="text-slate-600 mb-12">Feel free to drop a message! I’ll get back to you as soon as possible.</p>

      <form @submit.prevent="submitForm" class="grid gap-6 text-left animate-fade-in">
        <!-- Name -->
        <div>
          <label class="lg:block text-slate-700 font-medium mb-1 hidden">Name</label>
          <input
            v-model="form.name"
            type="text"
            placeholder="Your Name"
            class="w-full border border-slate-300 shadow-sm rounded-xl px-4 py-2 focus:ring-2 focus:ring-sky-500 outline-none transition duration-200"
            required
          />
        </div>

        <!-- Email -->
        <div>
          <label class="lg:block text-slate-700 font-medium mb-1 hidden">Email</label>
          <input
            v-model="form.email"
            type="email"
            placeholder="you@example.com"
            class="w-full border border-slate-300 shadow-sm rounded-xl px-4 py-2 focus:ring-2 focus:ring-sky-500 outline-none transition duration-200"
            required
          />
        </div>

        <!-- Message -->
        <div>
          <label class=" text-slate-700 font-medium mb-1 hidden lg:block">Message</label>
          <textarea
            v-model="form.message"
            rows="5"
            placeholder="Write your message..."
            class="w-full border border-slate-300 shadow-sm rounded-xl px-4 py-2 focus:ring-2 focus:ring-sky-500 outline-none transition duration-200 resize-none"
            required
          ></textarea>
        </div>

        <!-- Submit -->
        <button
          type="submit"
          class="bg-sky-600 hover:bg-sky-700 text-white font-semibold px-6 py-3 rounded-xl transition shadow-md hover:shadow-lg duration-300"
        >
          ✉️ Send Message
        </button>
      </form>

      <p v-if="submitted" class=" drop-shadow text-green-600 text-left mt-8 text-lg animate-fade-in fixed top-20 right-2 rounded bg-blue-100 p-5">
        ✅ Thank you! <br> I’ll get back to you soon.
      </p>
      <!-- <p v-if="successMessage" class=" drop-shadow text-green-600 text-left mt-8 text-lg animate-fade-in fixed top-20 right-2 rounded bg-blue-100 p-5">{{ successMessage }}</p> -->
    <p v-if="errorMessage" class=" drop-shadow text-green-600 text-left mt-8 text-lg animate-fade-in fixed top-20 right-2 rounded bg-blue-100 p-5">{{ errorMessage }}</p>
    </div>
    </div>
  </section>


</template>

<script>

export default {
  name: 'ContactForm',
  data() {
    return {
      form: {
        name: '',
        email: '',
        message: ''
      },
      successMessage: '', // ✅ Added
      errorMessage: '',   // ✅ Added
      submitted: false
    }
  },
  methods: {
    async submitForm() {
      try {
        let response = await axios.post('/contact', this.form)

        this.successMessage = response.data.message || 'Message sent successfully!'
        this.errorMessage = ''
        this.form = { name: '', email: '', message: '' } // ✅ Reset
        this.submitted = true
      } catch (error) {
        this.errorMessage = error.response?.data?.message || 'Something went wrong.'
        this.successMessage = ''
      }

      // ✅ Hide messages after 3 seconds
      setTimeout(() => {
        this.submitted = false
        this.successMessage = ''
        this.errorMessage = ''
      }, 3000)
    }
  }
}
</script>




<style scoped>
@keyframes fade-in {
  from {
    opacity: 0;
    transform: translateY(-10px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
.animate-fade-in {
  animation: fade-in 0.5s ease-out;
}
</style>



