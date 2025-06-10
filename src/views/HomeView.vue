<style>


.gradient-bg {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
}

.card-hover {
  transition: all 0.3s ease;
}

.card-hover:hover {
  transform: translateY(-8px);
  box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.25);
}

.typing-effect {
  overflow: hidden;
  border-right: 3px solid #667eea;
  white-space: nowrap;
  animation: typing 3.5s steps(40, end), blink-caret 0.75s step-end infinite;
}

@keyframes typing {
  from {
    width: 0;
  }
  to {
    width: 100%;
  }
}

@keyframes blink-caret {
  from, to {
    border-color: transparent;
  }
  50% {
    border-color: #667eea;
  }
}

.floating {
  animation: float 6s ease-in-out infinite;
}

@keyframes float {
  0%, 100% {
    transform: translateY(0px);
  }
  50% {
    transform: translateY(-20px);
  }
}

.glow {
  box-shadow: 0 0 20px rgba(102, 126, 234, 0.3);
}

.skill-bar {
  transition: width 2s ease-in-out;
}

.parallax {
  background-attachment: fixed;
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
}

.glass-effect {
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(10px);
  border: 1px solid rgba(255, 255, 255, 0.2);
}

.section-padding {
  padding: 5rem 0;
}

.smooth-scroll {
  scroll-behavior: smooth;
}
</style>

<template>
  <div class="smooth-scroll">
    <!-- Navigation -->
    <nav class="fixed top-0 w-full z-50 transition-all duration-300"
         :class="{'glass-effect': scrolled, 'bg-transparent': !scrolled}">
      <div class="container mx-auto px-6 py-4">
        <div class="flex justify-between md:justify-around items-center">
          <div class="text-2xl font-bold"><span
              class="bg-gradient-to-r from-purple-400 to-pink-400 bg-clip-text text-transparent">
            KENETH KIPYEGON
          </span>
          </div>

          <!-- Desktop Navigation -->
          <div class="hidden md:flex space-x-8">
            <a v-for="item in navItems" :key="item.id"
               @click="scrollToSection(item.id)"
               class="text-gray-300 hover:text-white cursor-pointer transition-colors duration-300 relative group">
              {{ item.name }}
              <span
                  class="absolute bottom-0 left-0 w-0 h-0.5 bg-gradient-to-r from-purple-400 to-pink-400 transition-all duration-300 group-hover:w-full"></span>
            </a>
          </div>

          <!-- Mobile Menu Button -->
          <button @click="mobileMenuOpen = !mobileMenuOpen" class="md:hidden text-white">
            <i class="fas fa-bars text-xl text-black"></i>
          </button>
        </div>

        <!-- Mobile Menu -->
        <div v-show="mobileMenuOpen" class="md:hidden mt-4 space-y-4">
          <a v-for="item in navItems" :key="item.id"
             @click="scrollToSection(item.id); mobileMenuOpen = false"
             class="block text-gray-600 hover:text-black cursor-pointer transition-colors duration-300">
            {{ item.name }}
          </a>
        </div>
      </div>
    </nav>

    <!-- Hero Section -->
    <section id="home" class="min-h-screen gradient-bg flex items-center justify-center relative overflow-hidden">
      <div class="absolute inset-0 opacity-10">
        <div class="floating absolute top-20 left-20 w-72 h-72 bg-white rounded-full"></div>
        <div class="floating absolute bottom-20 right-20 w-96 h-96 bg-pink-300 rounded-full"
             style="animation-delay: -2s;"></div>
        <div
            class="floating absolute top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2 w-64 h-64 bg-purple-300 rounded-full"
            style="animation-delay: -4s;"></div>
      </div>

      <div class="container mx-auto px-6 text-center text-white relative z-10">
        <div class="mb-8">
          <div class="w-48 h-48 mx-auto rounded-full overflow-hidden border-4 border-white/30 glow mb-8">
            <img src="/keneth.png"
                 alt="Keneth Kipyegon" class="w-full h-full object-cover">
          </div>
        </div>

        <h1 class="text-5xl md:text-7xl font-bold mb-6">
          Hi, I'm <span
            class="bg-gradient-to-r from-yellow-400 to-orange-400 bg-clip-text text-transparent">Keneth</span>
        </h1>

        <div class="text-xl md:text-2xl mb-8 h-16">
          <p class="typing-effect ">{{ currentRole }}</p>
        </div>

        <p class="text-lg md:text-xl mb-12 max-w-3xl mx-auto leading-relaxed text-start">
          Passionate  full-stack developer with expertise in both frontend and backend technologies. Specializing in
           secure coding practices, and innovative problem-solving.Committed to building robust,
          scalable applications that prioritize security and user experience.
        </p>

        <div class="flex flex-col sm:flex-row gap-4 justify-center">
          <button @click="scrollToSection('projects')"
                  class="px-8 py-4 bg-white text-purple-600 rounded-full font-semibold hover:bg-gray-100 transition-all duration-300 transform hover:scale-105">
            View My Work
          </button>
          <button @click="scrollToSection('contact')"
                  class="px-8 py-4 border-2 border-white text-white rounded-full font-semibold hover:bg-white hover:text-purple-600 transition-all duration-300 transform hover:scale-105">
            Let's Connect
          </button>
        </div>
      </div>
    </section>

    <!-- Resume Section -->
    <section id="resume" class="section-padding bg-gray-50">
      <div class="container mx-auto px-6">
        <h2 class="text-4xl md:text-5xl font-bold text-center mb-16 text-gray-800">
          Professional <span
            class="bg-gradient-to-r from-purple-600 to-pink-600 bg-clip-text text-transparent">Resume</span>
        </h2>

        <div class="grid md:grid-cols-2 gap-12">
          <!-- Education -->
          <div class="card-hover bg-white rounded-2xl p-8 shadow-lg">
            <h3 class="text-2xl font-bold mb-6 text-gray-800 flex items-center">
              <i class="fas fa-graduation-cap text-purple-600 mr-3"></i>
              Education
            </h3>
            <div class="space-y-6">
              <div class="border-l-4 border-purple-600 pl-6">
                <h4 class="text-xl font-semibold text-gray-800">Bachelor of Science in Computer Science</h4>
                <p class="text-purple-600 font-medium">University of Nairobi</p>
                <p class="text-gray-600">2020 - 2024</p>
                <p class="text-gray-700 mt-2">Focus on Cybersecurity, Software Engineering, and Data Structures</p>
              </div>
              <div class="border-l-4 border-purple-600 pl-6">
                <h4 class="text-xl font-semibold text-gray-800">Certified Ethical Hacker (CEH)</h4>
                <p class="text-purple-600 font-medium">EC-Council</p>
                <p class="text-gray-600">2023</p>
              </div>
            </div>
          </div>

          <!-- Experience -->
          <div class="card-hover bg-white rounded-2xl p-8 shadow-lg">
            <h3 class="text-2xl font-bold mb-6 text-gray-800 flex items-center">
              <i class="fas fa-briefcase text-purple-600 mr-3"></i>
              Experience
            </h3>
            <div class="space-y-6">
              <div class="border-l-4 border-purple-600 pl-6">
                <h4 class="text-xl font-semibold text-gray-800">Junior Cybersecurity Analyst</h4>
                <p class="text-purple-600 font-medium">SecureTech Solutions</p>
                <p class="text-gray-600">2024 - Present</p>
                <p class="text-gray-700 mt-2">Vulnerability assessments, incident response, and security monitoring</p>
              </div>
              <div class="border-l-4 border-purple-600 pl-6">
                <h4 class="text-xl font-semibold text-gray-800">Full-Stack Developer Intern</h4>
                <p class="text-purple-600 font-medium">InnovateLab Kenya</p>
                <p class="text-gray-600">2023 - 2024</p>
                <p class="text-gray-700 mt-2">Developed secure web applications using Vue.js, Node.js, and MongoDB</p>
              </div>
            </div>
          </div>
        </div>

        <!-- Skills -->
        <div class="mt-12">
          <h3 class="text-3xl font-bold text-center mb-12 text-gray-800">Technical Skills</h3>
          <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
            <div v-for="skillCategory in skills" :key="skillCategory.category"
                 class="card-hover bg-white rounded-2xl p-6 shadow-lg">
              <h4 class="text-xl font-semibold mb-4 text-gray-800 flex items-center">
                <i :class="skillCategory.icon + ' text-purple-600 mr-3'"></i>
                {{ skillCategory.category }}
              </h4>
              <div class="space-y-3">
                <div v-for="skill in skillCategory.items" :key="skill.name">
                  <div class="flex justify-between mb-1">
                    <span class="text-gray-700">{{ skill.name }}</span>
                    <span class="text-gray-500">{{ skill.level }}%</span>
                  </div>
                  <div class="w-full bg-gray-200 rounded-full h-2">
                    <div class="skill-bar bg-gradient-to-r from-purple-600 to-pink-600 h-2 rounded-full"
                         :style="{width: skill.level + '%'}"></div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Projects Section -->
    <section id="projects" class="section-padding bg-white">
      <div class="container mx-auto px-6">
        <h2 class="text-4xl md:text-5xl font-bold text-center mb-16 text-gray-800">
          Featured <span
            class="bg-gradient-to-r from-purple-600 to-pink-600 bg-clip-text text-transparent">Projects</span>
        </h2>

        <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
          <div v-for="project in projects" :key="project.id"
               class="card-hover bg-white rounded-2xl overflow-hidden shadow-lg border border-gray-100">
            <div class="h-48 bg-gradient-to-br from-purple-400 to-pink-400 flex items-center justify-center">
              <i :class="project.icon + ' text-6xl text-white'"></i>
            </div>
            <div class="p-6">
              <h3 class="text-xl font-bold mb-3 text-gray-800">{{ project.title }}</h3>
              <p class="text-gray-600 mb-4">{{ project.description }}</p>
              <div class="flex flex-wrap gap-2 mb-4">
                                <span v-for="tech in project.technologies" :key="tech"
                                      class="px-3 py-1 bg-purple-100 text-purple-600 rounded-full text-sm font-medium">
                                    {{ tech }}
                                </span>
              </div>
              <div class="flex space-x-4">
                <a :href="project.github" class="text-gray-600 hover:text-purple-600 transition-colors">
                  <i class="fab fa-github text-xl"></i>
                </a>
                <a :href="project.demo" class="text-gray-600 hover:text-purple-600 transition-colors">
                  <i class="fas fa-external-link-alt text-xl"></i>
                </a>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Lab Challenges Section -->
    <section id="challenges" class="section-padding bg-gray-50">
      <div class="container mx-auto px-6">
        <h2 class="text-4xl md:text-5xl font-bold text-center mb-16 text-gray-800">
          Lab <span class="bg-gradient-to-r from-purple-600 to-pink-600 bg-clip-text text-transparent">Challenges</span>
        </h2>

        <div class="space-y-8">
          <div v-for="challenge in labChallenges" :key="challenge.id"
               class="card-hover bg-white rounded-2xl p-8 shadow-lg">
            <div class="grid md:grid-cols-3 gap-8">
              <div class="md:col-span-2">
                <div class="flex items-center mb-4">
                  <i :class="challenge.icon + ' text-2xl text-purple-600 mr-3'"></i>
                  <h3 class="text-2xl font-bold text-gray-800">{{ challenge.title }}</h3>
                  <span :class="'px-3 py-1 rounded-full text-sm font-medium ml-auto ' + challenge.difficultyClass">
                                        {{ challenge.difficulty }}
                                    </span>
                </div>
                <p class="text-gray-600 mb-4">{{ challenge.description }}</p>

                <div class="mb-4">
                  <h4 class="font-semibold text-gray-800 mb-2">Approach & Solution:</h4>
                  <p class="text-gray-700">{{ challenge.solution }}</p>
                </div>

                <div class="mb-4">
                  <h4 class="font-semibold text-gray-800 mb-2">Tools Used:</h4>
                  <div class="flex flex-wrap gap-2">
                                        <span v-for="tool in challenge.tools" :key="tool"
                                              class="px-3 py-1 bg-gray-100 text-gray-700 rounded-full text-sm mono">
                                            {{ tool }}
                                        </span>
                  </div>
                </div>

                <div>
                  <h4 class="font-semibold text-gray-800 mb-2">Key Lessons:</h4>
                  <p class="text-gray-700 italic">{{ challenge.lessons }}</p>
                </div>
              </div>

              <div class="flex items-center justify-center">
                <div class="w-full h-48 bg-gray-900 rounded-lg flex items-center justify-center">
                  <i :class="challenge.icon + ' text-6xl text-green-400'"></i>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Contact Section -->
    <section id="contact" class="section-padding gradient-bg">
      <div class="container mx-auto px-6">
        <h2 class="text-4xl md:text-5xl font-bold text-center mb-16 text-white">
          Let's <span class="text-yellow-400">Connect</span>
        </h2>

        <div class="max-w-4xl mx-auto">
          <div class="text-center mb-12">
            <p class="text-xl text-gray-200 mb-8">
              Ready to collaborate on your next cybersecurity project or discuss innovative tech solutions?
              Let's build something amazing together!
            </p>
          </div>

          <div class="grid md:grid-cols-2 lg:grid-cols-4 gap-6">
            <a v-for="contact in contactInfo" :key="contact.platform"
               :href="contact.url" target="_blank"
               class="glass-effect rounded-2xl p-6 text-center hover:bg-white/20 transition-all duration-300 transform hover:scale-105">
              <i :class="contact.icon + ' text-4xl text-white mb-4'"></i>
              <h3 class="text-xl font-semibold text-white mb-2">{{ contact.platform }}</h3>
              <p class="text-gray-300">{{ contact.handle }}</p>
            </a>
          </div>

          <div class="text-center mt-12">
            <p class="text-gray-300 mb-4">Prefer email?</p>
            <a href="mailto:kenethkipyegon@gmail.com"
               class="inline-flex items-center px-8 py-4 bg-white text-purple-600 rounded-full font-semibold hover:bg-gray-100 transition-all duration-300 transform hover:scale-105">
              <i class="fas fa-envelope mr-3"></i>
              kenethkipyegon@gmail.com
            </a>
          </div>
        </div>
      </div>
    </section>

    <!-- Footer -->
    <footer class="bg-gray-900 text-white py-8">
      <div class="container mx-auto px-6 text-center">
        <p class="text-gray-400">
          &copy; {{ new Date().getFullYear() }} Keneth Kipyegon. Crafted with passion and purpose.
        </p>
      </div>
    </footer>
  </div>
</template>
<script lang="ts" setup>
import {ref, onMounted} from 'vue'

const scrolled = ref(false)
const mobileMenuOpen = ref(false)
const currentRole = ref('Full-Stack Developer')

const navItems = [
  {id: 'home', name: 'Home'},
  {id: 'resume', name: 'Resume'},
  {id: 'projects', name: 'Projects'},
  {id: 'challenges', name: 'Lab Challenges'},
  {id: 'contact', name: 'Contact'}
]

const skills = [
  {
    category: 'Cybersecurity',
    icon: 'fas fa-shield-alt',
    items: [
      {name: 'Penetration Testing', level: 85},
      {name: 'Vulnerability Assessment', level: 90},
      {name: 'Digital Forensics', level: 75},
      {name: 'Incident Response', level: 80}
    ]
  },
  {
    category: 'Programming',
    icon: 'fas fa-code',
    items: [
      {name: 'Python', level: 90},
      {name: 'JavaScript', level: 85},
      {name: 'Java', level: 80},
      {name: 'C++', level: 75}
    ]
  },
  {
    category: 'Web Development',
    icon: 'fas fa-globe',
    items: [
      {name: 'Vue.js', level: 85},
      {name: 'Node.js', level: 80},
      {name: 'MongoDB', level: 75},
      {name: 'MySQL', level: 85}
    ]
  }
]

const projects = [
  {
    id: 1,
    title: 'SecureAuth System',
    description: 'Multi-factor authentication system with biometric integration and real-time threat detection.',
    technologies: ['Vue.js', 'Node.js', 'MongoDB', 'WebAuthn'],
    icon: 'fas fa-lock',
    github: '#',
    demo: '#'
  },
  {
    id: 2,
    title: 'Network Vulnerability Scanner',
    description: 'Automated network scanning tool for identifying security vulnerabilities and generating detailed reports.',
    technologies: ['Python', 'Nmap', 'SQLite', 'Flask'],
    icon: 'fas fa-network-wired',
    github: '#',
    demo: '#'
  },
  {
    id: 3,
    title: 'E-Commerce Security Platform',
    description: 'Secure e-commerce platform with encrypted transactions and fraud detection algorithms.',
    technologies: ['React', 'Express.js', 'PostgreSQL', 'Stripe'],
    icon: 'fas fa-shopping-cart',
    github: '#',
    demo: '#'
  }
]

const labChallenges = [
  {
    id: 1,
    title: 'SQL Injection CTF Challenge',
    description: 'A web application with multiple SQL injection vulnerabilities requiring different bypass techniques.',
    difficulty: 'Hard',
    difficultyClass: 'bg-red-100 text-red-600',
    icon: 'fas fa-database',
    solution: 'Utilized UNION-based injection to extract database schema, then employed time-based blind injection for data exfiltration. Bypassed WAF using comment obfuscation and encoding techniques.',
    tools: ['Burp Suite', 'SQLmap', 'Custom Python Scripts', 'Postman'],
    lessons: 'Understanding different injection types and defense mechanisms is crucial for both attack and protection strategies.'
  },
  {
    id: 2,
    title: 'Buffer Overflow Exploitation',
    description: 'Binary exploitation challenge requiring identification and exploitation of buffer overflow vulnerabilities.',
    difficulty: 'Expert',
    difficultyClass: 'bg-purple-100 text-purple-600',
    icon: 'fas fa-bug',
    solution: 'Analyzed binary with GDB, identified vulnerable function, crafted shellcode payload, and successfully gained shell access by overwriting return address.',
    tools: ['GDB', 'objdump', 'Python', 'pwntools', 'Ghidra'],
    lessons: 'Memory management and assembly language knowledge are fundamental for low-level security analysis.'
  },
  {
    id: 3,
    title: 'Cryptographic Hash Collision',
    description: 'Challenge involving finding hash collisions and exploiting cryptographic weaknesses in custom implementation.',
    difficulty: 'Medium',
    difficultyClass: 'bg-yellow-100 text-yellow-600',
    icon: 'fas fa-key',
    solution: 'Analyzed the custom hash function implementation, identified weak collision resistance, and used birthday attack principles to generate colliding inputs.',
    tools: ['Python', 'Hashcat', 'John the Ripper', 'Custom Scripts'],
    lessons: 'Cryptographic implementations require careful analysis; even small weaknesses can be exploited effectively.'
  }
]

const contactInfo = [
  {
    platform: 'LinkedIn',
    handle: '@kenethkipyegon',
    url: 'https://www.linkedin.com/in/kipyegon-keneth-8b19b8195/',
    icon: 'fab fa-linkedin'
  },
  {
    platform: 'GitHub',
    handle: '@kenethkipyegon',
    url: 'https://github.com/keneth217',
    icon: 'fab fa-github'
  },
  {
    platform: 'Articles',
    handle: '@kenethkipyegon',
    url: 'https://www.kenethkipyegon.com',
    icon: 'fas fa-pen-nib'
  },
  {
    platform: 'Phone',
    handle: '+254 711766223',
    url: 'tel:+254 711766223',
    icon: 'fas fa-phone'
  }
]

function handleScroll() {
  scrolled.value = window.scrollY > 50
}

function scrollToSection(sectionId: string) {
  const element = document.getElementById(sectionId)
  if (element) {
    element.scrollIntoView({behavior: 'smooth'})
  }
}

function typeWriterEffect() {
  const roles = [
    'Full-Stack Developer',
    'Life  Long Learner',
    'Cyber  Security Enthusiast & Problem Solver',
    'Technical Writer and Tech Innovator'
  ]
  let currentIndex = 0
  setInterval(() => {
    currentIndex = (currentIndex + 1) % roles.length
    currentRole.value = roles[currentIndex]
  }, 4000)
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
  typeWriterEffect()
})
</script>

