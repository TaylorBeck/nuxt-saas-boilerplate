<template>
  <div class="font-sans bg-gray-50">
    <!-- Header -->
    <header class="bg-white shadow-md fixed w-full z-10 transition-all duration-300" :class="{ 'bg-opacity-90 backdrop-blur-md': scrolled }">
      <nav class="container mx-auto px-6 py-4 flex justify-between items-center">
        <div class="text-2xl font-bold text-blue-600">YourLogo</div>
        <div class="hidden md:flex space-x-6">
          <a v-for="item in navItems" :key="item" :href="`#${item.toLowerCase()}`" class="text-gray-700 hover:text-blue-600 transition duration-300">{{ item }}</a>
        </div>
        <a href="#contact" class="hidden md:block bg-blue-600 text-white px-6 py-2 rounded-full hover:bg-blue-700 transition duration-300">Get Started</a>
      </nav>
    </header>

    <!-- Hero Section -->
    <section class="pt-32 pb-20 bg-gradient-to-br from-blue-600 to-indigo-700 text-white">
      <div class="container mx-auto px-6 flex flex-col md:flex-row items-center">
        <div class="md:w-1/2 mb-10 md:mb-0">
          <h1 class="text-4xl md:text-6xl font-bold mb-6 leading-tight">Transform Your Business with Our Solution</h1>
          <p class="text-xl mb-8 text-blue-100">Discover how our innovative platform can elevate your company to new heights.</p>
          <a href="#" class="bg-white text-blue-600 py-3 px-8 rounded-full text-lg font-semibold hover:bg-blue-50 transition duration-300 inline-block">Get Started</a>
        </div>
        <div class="md:w-1/2">
          <img src="https://via.placeholder.com/600x400" alt="Hero Image" class="rounded-lg shadow-2xl">
        </div>
      </div>
    </section>

    <!-- Features -->
    <section id="features" class="py-20">
      <div class="container mx-auto px-6">
        <h2 class="text-3xl font-bold text-center text-gray-800 mb-12">Key Features</h2>
        <div class="grid grid-cols-1 md:grid-cols-3 gap-12">
          <div v-for="feature in features" :key="feature.title" class="bg-white p-8 rounded-xl shadow-lg hover:shadow-xl transition duration-300">
            <div class="text-blue-600 mb-4">
              <component :is="feature.icon" class="w-12 h-12" />
            </div>
            <h3 class="text-xl font-semibold mb-4">{{ feature.title }}</h3>
            <p class="text-gray-600">{{ feature.description }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- Pricing -->
    <section id="pricing" class="py-20 bg-gray-100">
      <div class="container mx-auto px-6">
        <h2 class="text-3xl font-bold text-center text-gray-800 mb-12">Pricing Plans</h2>
        <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
          <div v-for="plan in pricingPlans" :key="plan.title" class="bg-white p-8 rounded-xl shadow-lg hover:shadow-xl transition duration-300">
            <h3 class="text-2xl font-semibold mb-4">{{ plan.title }}</h3>
            <p class="text-4xl font-bold mb-6">{{ plan.price }}<span class="text-sm font-normal text-gray-600">/month</span></p>
            <ul class="mb-8">
              <li v-for="feature in plan.features" :key="feature" class="flex items-center mb-2">
                <svg class="w-5 h-5 text-green-500 mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7"></path></svg>
                {{ feature }}
              </li>
            </ul>
            <a :href="plan.link" class="block text-center bg-blue-600 text-white py-3 rounded-lg hover:bg-blue-700 transition duration-300">Choose Plan</a>
          </div>
        </div>
      </div>
    </section>

    <!-- Testimonials -->
    <section id="testimonials" class="py-20">
      <div class="container mx-auto px-6">
        <h2 class="text-3xl font-bold text-center text-gray-800 mb-12">What Our Clients Say</h2>
        <div class="grid grid-cols-1 md:grid-cols-2 gap-12">
          <div v-for="testimonial in testimonials" :key="testimonial.name" class="bg-white p-8 rounded-xl shadow-lg hover:shadow-xl transition duration-300">
            <p class="text-gray-600 mb-6 italic">"{{ testimonial.quote }}"</p>
            <div class="flex items-center">
              <img :src="testimonial.avatar" :alt="testimonial.name" class="w-12 h-12 rounded-full mr-4">
              <div>
                <p class="font-semibold">{{ testimonial.name }}</p>
                <p class="text-gray-600">{{ testimonial.position }}</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Contact  -->
    <section id="contact" class="py-20 bg-blue-600">
      <div class="container mx-auto px-6">
        <h2 class="text-3xl font-bold text-center text-white mb-12">Get in Touch</h2>
        <div class="max-w-lg mx-auto bg-white rounded-xl shadow-lg p-8">
          <form @submit.prevent="submitForm">
            <div class="mb-6">
              <label for="name" class="block text-gray-700 font-bold mb-2">Name</label>
              <input type="text" id="name" v-model="form.name" class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-600" required>
            </div>
            <div class="mb-6">
              <label for="email" class="block text-gray-700 font-bold mb-2">Email</label>
              <input type="email" id="email" v-model="form.email" class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-600" required>
            </div>
            <div class="mb-6">
              <label for="message" class="block text-gray-700 font-bold mb-2">Message</label>
              <textarea id="message" v-model="form.message" rows="4" class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-600" required></textarea>
            </div>
            <button type="submit" class="w-full bg-blue-600 text-white py-3 px-4 rounded-lg hover:bg-blue-700 transition duration-300">Send Message</button>
          </form>
        </div>
      </div>
    </section>

    <!-- Footer -->
    <footer class="bg-gray-800 text-white py-12">
      <div class="container mx-auto px-6">
        <div class="grid grid-cols-1 md:grid-cols-4 gap-8">
          <div>
            <h3 class="text-xl font-bold mb-4">YourLogo</h3>
            <p class="text-gray-400">Transforming businesses with innovative solutions.</p>
          </div>
          <div>
            <h4 class="text-lg font-semibold mb-4">Quick Links</h4>
            <ul class="space-y-2">
              <li v-for="item in navItems" :key="item"><a :href="`#${item.toLowerCase()}`" class="text-gray-400 hover:text-white transition duration-300">{{ item }}</a></li>
            </ul>
          </div>
          <div>
            <h4 class="text-lg font-semibold mb-4">Connect</h4>
            <ul class="space-y-2">
              <li><a href="#" class="text-gray-400 hover:text-white transition duration-300">Twitter</a></li>
              <li><a href="#" class="text-gray-400 hover:text-white transition duration-300">LinkedIn</a></li>
              <li><a href="#" class="text-gray-400 hover:text-white transition duration-300">Facebook</a></li>
            </ul>
          </div>
          <div>
            <h4 class="text-lg font-semibold mb-4">Contact</h4>
            <p class="text-gray-400">123 Business Street</p>
            <p class="text-gray-400">City, State 12345</p>
            <p class="text-gray-400">contact@yourcompany.com</p>
          </div>
        </div>
        <div class="mt-12 text-center text-gray-400">
          <p>&copy; 2024 YourCompany. All rights reserved.</p>
        </div>
      </div>
    </footer>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const navItems = ['Features', 'Pricing', 'Testimonials', 'Contact']

const features = [
  { title: 'Advanced Analytics', description: 'Gain deep insights into your business performance with our cutting-edge analytics tools.', icon: 'ChartBarIcon' },
  { title: 'Cloud Integration', description: 'Seamlessly integrate with popular cloud services for enhanced productivity.', icon: 'CloudIcon' },
  { title: '24/7 Support', description: 'Our dedicated support team is always ready to assist you, anytime, anywhere.', icon: 'SupportIcon' }
]

const pricingPlans = [
  { title: 'Basic', price: '$9.99', features: ['Feature 1', 'Feature 2', 'Feature 3'], link: '#' },
  { title: 'Pro', price: '$19.99', features: ['Feature 1', 'Feature 2', 'Feature 3', 'Feature 4'], link: '#' },
  { title: 'Enterprise', price: '$29.99', features: ['Feature 1', 'Feature 2', 'Feature 3', 'Feature 4', 'Feature 5'], link: '#' }
]

const testimonials = [
  { name: 'John Doe', position: 'CEO, TechCorp', quote: 'This solution has revolutionized our business processes. Highly recommended!', avatar: 'https://via.placeholder.com/100' },
  { name: 'Jane Smith', position: 'CTO, InnovateCo', quote: 'The features and support provided are unparalleled. A game-changer for our company.', avatar: 'https://via.placeholder.com/100' }
]

const form = ref({
  name: '',
  email: '',
  message: ''
})

const submitForm = () => {
  // Handle form submission
  console.log('Form submitted:', form.value)
  // Reset form
  form.value = { name: '', email: '', message: '' }
}

const scrolled = ref(false)

const handleScroll = () => {
  scrolled.value = window.scrollY > 50
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>