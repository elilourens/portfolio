<script setup lang="ts">
// Cursor spotlight
const cursorX = ref('50vw')
const cursorY = ref('50vh')

onMounted(() => {
  const handler = (e: MouseEvent) => {
    cursorX.value = e.clientX + 'px'
    cursorY.value = e.clientY + 'px'
    document.documentElement.style.setProperty('--cursor-x', cursorX.value)
    document.documentElement.style.setProperty('--cursor-y', cursorY.value)
  }
  window.addEventListener('mousemove', handler)
  onUnmounted(() => window.removeEventListener('mousemove', handler))
})

const skills = [
  { icon: 'i-simple-icons-vuedotjs', name: 'Vue.js', level: 'Expert' },
  { icon: 'i-simple-icons-python', name: 'Python', level: 'Expert' },
  { icon: 'i-simple-icons-typescript', name: 'TypeScript', level: 'Advanced' },
  { icon: 'i-simple-icons-nuxtdotjs', name: 'Nuxt', level: 'Advanced' },
  { icon: 'i-simple-icons-langchain', name: 'LangChain', level: 'Advanced' },
  { icon: 'i-simple-icons-fastapi', name: 'FastAPI', level: 'Advanced' },
  { icon: 'i-simple-icons-tailwindcss', name: 'Tailwind CSS', level: 'Advanced' },
  { icon: 'i-simple-icons-postgresql', name: 'PostgreSQL', level: 'Advanced' },
  { icon: 'i-simple-icons-supabase', name: 'Supabase', level: 'Advanced' },
  { icon: 'i-simple-icons-microsoftazure', name: 'Azure', level: 'Intermediate' },
  { icon: 'i-simple-icons-amazonaws', name: 'AWS Bedrock', level: 'Intermediate' },
  { icon: 'i-simple-icons-docker', name: 'Docker', level: 'Intermediate' }
]

const experience = [
  {
    company: 'Barclays',
    role: 'Technology Developer Intern – AI/ML',
    period: 'June – August 2025',
    location: 'Glasgow, Scotland',
    bullets: [
      'Highest scoring candidate in the Barclays recruitment process. Joined the Chief Technology Office AI/ML team.',
      'Developed an NLP-powered smart router to dynamically select relevant vector databases during the RAG phase, improving response relevancy with a multi-shot approach.',
      'Built an AI Agent Evaluation framework measuring cost, latency, and chain-of-thought decision making.',
      'Stack: Python, LangChain, LangGraph, AWS Bedrock.'
    ]
  },
  {
    company: 'Uniper',
    role: 'Software Engineering Intern',
    period: 'September 2023 – August 2024',
    location: 'Birmingham, England',
    bullets: [
      'Revamped a full-stack trading application for the business division, doubling active users and significantly reducing load times through optimised data retrieval.',
      'Built Vue.js frontends and Python/C# backends deployed on Azure Cloud.',
      'Managed Postgres databases, designing SQL stored procedures for custom APIs.',
      'Implemented Azure RBAC and scalable serverless architecture.',
      'Earned Microsoft AZ-900: Azure Fundamentals certification.'
    ]
  }
]

const hackathons = [
  {
    event: 'HackEurope',
    result: '🏆 1st Place – Monzo Fintech Track',
    prize: '€1,000',
    period: 'February 2026 · Dublin, Ireland',
    description: 'Built Prophit in 30 hours – a spending prediction app that analyses your past transactions against public datasets (weather, events, calendar) to forecast tomorrow\'s spending. Judged by Monzo\'s CEO, Susquehanna, and Red Hat. 750+ competitors across Dublin, Paris, and Stockholm.',
    slug: '/projects/prophit'
  },
  {
    event: 'JP Morgan – Code for Good',
    result: '🥈 2nd Place',
    prize: '',
    period: 'October 2024 · Glasgow, Scotland',
    description: 'Built a website and mobile app for the environmental charity Another Way in 24 hours. Added gamification (XP systems, tasks, store) and a Python/BeautifulSoup web scraper for regional UK climate data. React Native frontend.'
  }
]

const timeline = [
  { label: 'Computing Prize', text: 'Top of class, University of Stirling' },
  { label: 'Turing Grant', text: 'Study abroad at Lingnan University, Hong Kong' },
  { label: 'Barclays', text: 'Highest scoring candidate in the recruitment process' },
  { label: 'HackEurope 2026', text: '1st place, €1,000 – Monzo Fintech Track' }
]
</script>

<template>
  <div
    class="spotlight relative flex flex-col gap-2 p-3 md:overflow-hidden md:h-full"
    style="background-color: #09090b; background-image: radial-gradient(rgba(250, 204, 21, 0.09) 1px, transparent 1px); background-size: 28px 28px;"
  >

    <!-- ROW 1: Hero + Stats -->
    <div class="flex flex-col md:flex-row gap-2 shrink-0">
      <div class="flex-1 border border-neutral-800 bg-neutral-950 p-5 flex items-center justify-between gap-4 hover:shadow-[3px_3px_0_rgba(250,204,21,0.35)] hover:-translate-x-px hover:-translate-y-px transition-all duration-200">
        <div>
          <div class="text-[10px] font-mono text-neutral-400 uppercase tracking-[0.2em] flex items-center gap-1.5 mb-2">
            <span class="w-1.5 h-1.5 bg-yellow-400 inline-block shrink-0 pulse-ring"></span>
            Portfolio · {{ new Date().getFullYear() }}
          </div>
          <h1 class="text-4xl md:text-5xl font-black tracking-tight leading-none text-white">
            Eli <span class="underline underline-offset-4 decoration-2 decoration-yellow-400">Lourens</span>
          </h1>
          <p class="text-sm text-neutral-400 mt-1.5">Final-year CS student · AI engineer · HackEurope 2026 winner</p>
        </div>
        <div class="hidden sm:flex gap-2 shrink-0">
          <UButton size="sm" color="neutral" label="Barclays · Uniper" icon="i-lucide-briefcase" />
          <UButton size="sm" color="neutral" variant="outline" label="Stirling, Scotland" icon="i-lucide-map-pin" />
        </div>
      </div>

      <div class="flex gap-px bg-neutral-800 border border-neutral-800 md:shrink-0">
        <div class="bg-neutral-950 flex-1 md:flex-none px-4 md:px-6 py-4 flex flex-col justify-center">
          <div class="text-2xl font-black text-white leading-none">€1k</div>
          <div class="text-[9px] text-yellow-400 uppercase tracking-widest mt-1">Won @ HackEurope</div>
        </div>
        <div class="bg-neutral-950 flex-1 md:flex-none px-4 md:px-6 py-4 flex flex-col justify-center">
          <div class="text-2xl font-black text-white leading-none">2</div>
          <div class="text-[9px] text-neutral-400 uppercase tracking-widest mt-1">Internships</div>
        </div>
        <div class="bg-neutral-950 flex-1 md:flex-none px-4 md:px-6 py-4 flex flex-col justify-center">
          <div class="flex items-center gap-1.5 leading-none">
            <UIcon name="i-simple-icons-microsoftazure" class="text-blue-400 size-5 shrink-0" />
            <div class="text-lg font-black text-white">AZ-900</div>
          </div>
          <div class="text-[9px] text-neutral-400 uppercase tracking-widest mt-1">Azure Certified</div>
        </div>
      </div>
    </div>

    <!-- ROW 2: Main grid -->
    <div class="flex flex-col md:flex-row gap-2 md:flex-1 md:min-h-0">

      <!-- Left column -->
      <div class="md:flex-1 flex flex-col gap-2 md:min-h-0">

        <!-- 4 section cards -->
        <div class="grid grid-cols-2 md:grid-cols-4 gap-2 shrink-0">

          <!-- ABOUT -->
          <UModal size="lg">
            <div class="border border-neutral-800 bg-neutral-950 p-4 cursor-pointer hover:border-yellow-400 hover:bg-white hover:shadow-[3px_3px_0_rgba(250,204,21,0.4)] hover:-translate-x-px hover:-translate-y-px transition-all duration-200 group">
              <div class="text-[9px] font-mono text-neutral-400 group-hover:text-black uppercase tracking-[0.2em] mb-2">01</div>
              <h3 class="font-bold text-sm mb-1 text-white group-hover:text-black">About</h3>
              <p class="text-[11px] text-neutral-400 group-hover:text-black leading-relaxed">CS · Barclays · Uniper · Hong Kong</p>
              <div class="flex items-center justify-between mt-3">
                <div class="flex gap-1">
                  <span class="text-[9px] bg-neutral-800 text-neutral-300 group-hover:text-black px-1.5 py-0.5 font-mono">BSc CS</span>
                  <span class="text-[9px] bg-yellow-400 text-black px-1.5 py-0.5 font-mono">2026</span>
                </div>
                <UIcon name="i-lucide-arrow-up-right" class="size-3 text-neutral-500 group-hover:text-yellow-400 transition-colors" />
              </div>
            </div>
            <template #content>
              <div class="bg-neutral-950 p-6 max-h-[80vh] overflow-y-auto space-y-6">
                <div class="flex items-start gap-4 pb-5 border-b border-neutral-800">
                  <img src="/eli.jpg" alt="Eli Lourens" class="w-20 h-20 object-cover object-top shrink-0" />
                  <div>
                    <h2 class="text-2xl font-black text-white">Eli Lourens</h2>
                    <p class="text-sm text-neutral-400 mb-2">Final-year Computer Science student</p>
                    <div class="flex flex-wrap gap-1">
                      <UBadge label="Stirling, Scotland" color="neutral" variant="subtle" size="xs" />
                      <UBadge label="From South Africa" color="neutral" variant="subtle" size="xs" />
                      <UBadge label="BSc CS, 2026" color="neutral" variant="subtle" size="xs" />
                      <UBadge label="Open to work" size="xs" class="bg-yellow-400 text-black border-0" />
                    </div>
                  </div>
                </div>
                <div class="space-y-3 text-sm text-white leading-relaxed">
                  <p>I'm finishing my CS degree at Stirling in 2026. Did a placement year at Uniper working on trading tools (Vue, Python, C#, Azure), then a summer at Barclays on the AI team doing RAG pipelines and agent evaluation with LangChain, LangGraph, and AWS Bedrock.</p>
                  <p>Won HackEurope 2026 in Dublin out of 750+ competitors with a fintech app judged by Monzo's CEO. Also came 2nd at JP Morgan's Code for Good. I build things: a semantic file search tool that's live, a marketplace for reselling LLM API credits, a uni chatbot.</p>
                  <p>Top of my class, Computing Prize, Turing grant to study at Lingnan University in Hong Kong. Did the Bloomberg Trading Challenge representing Stirling.</p>
                </div>
                <div class="grid grid-cols-3 gap-px bg-neutral-200 border border-neutral-200">
                  <div class="bg-neutral-950 p-4">
                    <div class="text-2xl font-black text-white">€1k</div>
                    <div class="text-[10px] text-neutral-400 uppercase mt-1">HackEurope prize</div>
                  </div>
                  <div class="bg-neutral-950 p-4">
                    <div class="text-2xl font-black text-white">2</div>
                    <div class="text-[10px] text-neutral-400 uppercase mt-1">Internships</div>
                  </div>
                  <div class="bg-neutral-950 p-4">
                    <div class="text-2xl font-black text-white">#1</div>
                    <div class="text-[10px] text-neutral-400 uppercase mt-1">Barclays intake</div>
                  </div>
                </div>
                <div class="border border-neutral-800 bg-neutral-950 divide-y divide-neutral-800">
                  <div
                    v-for="item in timeline"
                    :key="item.label"
                    class="flex items-center gap-4 px-4 py-2.5 hover:bg-white transition-colors group/row"
                  >
                    <div class="text-xs text-white group-hover/row:text-black w-28 shrink-0 font-semibold">{{ item.label }}</div>
                    <div class="w-1.5 h-1.5 bg-yellow-400 shrink-0"></div>
                    <div class="text-sm text-neutral-300 group-hover/row:text-black">{{ item.text }}</div>
                  </div>
                </div>
              </div>
            </template>
          </UModal>

          <!-- EXPERIENCE -->
          <UModal size="xl">
            <div class="border border-neutral-800 bg-neutral-950 p-4 cursor-pointer hover:border-yellow-400 hover:bg-white hover:shadow-[3px_3px_0_rgba(250,204,21,0.4)] hover:-translate-x-px hover:-translate-y-px transition-all duration-200 group">
              <div class="text-[9px] font-mono text-neutral-400 group-hover:text-black uppercase tracking-[0.2em] mb-2">02</div>
              <h3 class="font-bold text-sm mb-1 text-white group-hover:text-black">Experience</h3>
              <p class="text-[11px] text-neutral-400 group-hover:text-black leading-relaxed">Barclays AI/ML · Uniper SE</p>
              <div class="flex items-center justify-between mt-3">
                <div class="flex gap-1">
                  <span class="text-[9px] bg-neutral-800 text-neutral-300 group-hover:text-black px-1.5 py-0.5 font-mono">Barclays</span>
                  <span class="text-[9px] bg-neutral-800 text-neutral-300 group-hover:text-black px-1.5 py-0.5 font-mono">Uniper</span>
                </div>
                <UIcon name="i-lucide-arrow-up-right" class="size-3 text-neutral-300 group-hover:text-yellow-400 transition-colors" />
              </div>
            </div>
            <template #content>
              <div class="bg-neutral-950 p-6 max-h-[80vh] overflow-y-auto">
                <h2 class="text-2xl font-black text-white mb-6">Experience</h2>
                <div class="space-y-8">
                  <div v-for="(job, i) in experience" :key="job.company" class="flex gap-6">
                    <div class="flex flex-col items-center">
                      <div class="w-2.5 h-2.5 bg-yellow-400 mt-1.5 shrink-0"></div>
                      <div v-if="i < experience.length - 1" class="w-px bg-neutral-700 flex-1 mt-2"></div>
                    </div>
                    <div class="flex-1 pb-4">
                      <div class="flex items-start justify-between mb-3">
                        <div>
                          <h3 class="font-bold text-lg text-white">{{ job.company }}</h3>
                          <p class="text-sm text-yellow-400 font-semibold">{{ job.role }}</p>
                        </div>
                        <div class="text-right shrink-0">
                          <p class="font-mono text-xs text-neutral-400">{{ job.period }}</p>
                          <p class="text-xs text-neutral-400">{{ job.location }}</p>
                        </div>
                      </div>
                      <ul class="space-y-2">
                        <li
                          v-for="(bullet, bi) in job.bullets"
                          :key="bullet"
                          class="flex gap-2 items-start text-sm text-neutral-300"
                          :class="bi === 0 ? 'bg-yellow-400/10 border-l-2 border-yellow-400 pl-3 py-1.5' : ''"
                        >
                          <UIcon name="i-lucide-chevron-right" class="text-yellow-400 size-4 mt-0.5 shrink-0" />
                          <span>{{ bullet }}</span>
                        </li>
                      </ul>
                    </div>
                  </div>
                </div>
              </div>
            </template>
          </UModal>

          <!-- SKILLS -->
          <UModal size="xl">
            <div class="border border-neutral-800 bg-neutral-950 p-4 cursor-pointer hover:border-yellow-400 hover:bg-white hover:shadow-[3px_3px_0_rgba(250,204,21,0.4)] hover:-translate-x-px hover:-translate-y-px transition-all duration-200 group">
              <div class="text-[9px] font-mono text-neutral-400 group-hover:text-black uppercase tracking-[0.2em] mb-2">03</div>
              <h3 class="font-bold text-sm mb-1 text-white group-hover:text-black">Skills</h3>
              <p class="text-[11px] text-neutral-400 group-hover:text-black leading-relaxed">Vue · Python · TS · LangChain</p>
              <div class="flex items-center justify-between mt-3">
                <div class="flex gap-1.5">
                  <UIcon name="i-simple-icons-vuedotjs" class="size-3.5 text-neutral-400 group-hover:text-black" />
                  <UIcon name="i-simple-icons-python" class="size-3.5 text-neutral-400 group-hover:text-black" />
                  <UIcon name="i-simple-icons-typescript" class="size-3.5 text-neutral-400 group-hover:text-black" />
                  <UIcon name="i-simple-icons-fastapi" class="size-3.5 text-neutral-400 group-hover:text-black" />
                </div>
                <UIcon name="i-lucide-arrow-up-right" class="size-3 text-neutral-300 group-hover:text-yellow-400 transition-colors" />
              </div>
            </div>
            <template #content>
              <div class="bg-neutral-950 p-6">
                <h2 class="text-2xl font-black text-white mb-6">Skills</h2>
                <div class="grid grid-cols-4 gap-px bg-neutral-950 border border-neutral-900">
                  <div
                    v-for="(skill, si) in skills"
                    :key="skill.name"
                    class="bg-neutral-950 flex flex-col items-center gap-2 p-5 hover:bg-neutral-900 transition-colors"
                    :class="si === 0 ? 'border-t-2 border-t-yellow-400' : ''"
                  >
                    <UIcon :name="skill.icon" class="size-8 text-yellow-400" />
                    <span class="text-sm font-semibold text-white text-center">{{ skill.name }}</span>
                  </div>
                </div>
              </div>
            </template>
          </UModal>

          <!-- HACKATHONS -->
          <UModal size="lg">
            <div class="border border-neutral-800 bg-neutral-950 p-4 cursor-pointer hover:border-yellow-400 hover:bg-white hover:shadow-[3px_3px_0_rgba(250,204,21,0.4)] hover:-translate-x-px hover:-translate-y-px transition-all duration-200 group">
              <div class="text-[9px] font-mono text-neutral-400 group-hover:text-black uppercase tracking-[0.2em] mb-2">04</div>
              <h3 class="font-bold text-sm mb-1 text-white group-hover:text-black">Hackathons</h3>
              <p class="text-[11px] text-neutral-400 group-hover:text-black leading-relaxed">🏆 HackEurope · 🥈 JP Morgan</p>
              <div class="flex items-center justify-between mt-3">
                <span class="text-[9px] bg-yellow-400 text-black px-1.5 py-0.5 font-mono font-bold">€1,000</span>
                <UIcon name="i-lucide-arrow-up-right" class="size-3 text-neutral-300 group-hover:text-yellow-400 transition-colors" />
              </div>
            </div>
            <template #content>
              <div class="bg-neutral-950 p-6 max-h-[80vh] overflow-y-auto space-y-4">
                <h2 class="text-2xl font-black text-white">Hackathons</h2>
                <div v-for="h in hackathons" :key="h.event" class="border border-neutral-800 bg-neutral-950 p-5 space-y-3">
                  <div v-if="h.event === 'HackEurope'" class="flex items-center gap-2 pb-3 border-b border-yellow-400/30">
                    <div class="w-1 h-4 bg-yellow-400 shrink-0"></div>
                    <span class="text-xs text-yellow-400 font-mono uppercase tracking-widest">HackEurope 2026 · Dublin · 1st Place</span>
                  </div>
                  <div class="flex items-start justify-between gap-3">
                    <div class="flex items-center gap-2 flex-wrap">
                      <UIcon v-if="h.event === 'HackEurope'" name="i-lucide-trophy" class="text-yellow-400 size-5 shrink-0" />
                      <h3 class="font-bold text-white">{{ h.event }}</h3>
                      <span class="text-xs font-bold text-yellow-400">{{ h.result }}</span>
                      <UBadge v-if="h.prize" :label="h.prize" color="neutral" variant="outline" size="sm" class="border-neutral-600 text-white" />
                    </div>
                    <p class="text-xs text-neutral-400 shrink-0 pt-0.5">{{ h.period }}</p>
                  </div>
                  <p class="text-sm text-neutral-300 leading-relaxed">{{ h.description }}</p>
                  <NuxtLink v-if="h.slug" :to="h.slug">
                    <UButton label="Full case study" trailing-icon="i-lucide-arrow-right" size="sm" variant="outline" color="neutral" class="border-neutral-600 text-white hover:bg-neutral-800" />
                  </NuxtLink>
                </div>
              </div>
            </template>
          </UModal>

        </div>

        <!-- Project cards row -->
        <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-2 md:flex-1 md:min-h-0">

          <!-- LLM RECYCLER -->
          <UModal size="xl">
            <div class="min-h-32 md:h-full border border-neutral-800 bg-neutral-950 p-4 cursor-pointer hover:border-yellow-400 hover:shadow-[3px_3px_0_rgba(250,204,21,0.4)] hover:-translate-x-px hover:-translate-y-px transition-all duration-200 group flex flex-col">
              <div class="flex items-center gap-2 mb-2">
                <UIcon name="i-lucide-recycle" class="text-yellow-400 size-4 shrink-0" />
                <h3 class="font-bold text-sm text-white">LLM Recycler</h3>
              </div>
              <p class="text-[11px] text-yellow-400 font-semibold mb-1">apirecycler.com</p>
              <p class="text-[11px] text-neutral-400 leading-relaxed flex-1">Marketplace for unused AI API credits. Buy, sell, proxy.</p>
              <div class="flex flex-wrap gap-1 mt-3">
                <span v-for="t in ['TypeScript', 'Vue', 'Hono', 'Stripe']" :key="t" class="font-mono text-[9px] text-neutral-400 border border-neutral-700 px-1.5 py-0.5">{{ t }}</span>
              </div>
              <UIcon name="i-lucide-arrow-up-right" class="size-3 text-neutral-600 mt-2 group-hover:text-yellow-400 transition-colors self-end" />
            </div>
            <template #content>
              <div class="bg-neutral-950 p-6 max-h-[80vh] overflow-y-auto space-y-5">
                <div>
                  <h2 class="text-2xl font-black text-white">LLM Recycler</h2>
                  <p class="text-sm text-yellow-400 font-semibold">apirecycler.com: Marketplace for LLM API credits</p>
                </div>
                <p class="text-sm text-neutral-300 leading-relaxed">Buy, sell, and proxy unused AI API credits. Many developers and companies have unused quota sitting idle. LLM Recycler creates a marketplace to trade those credits, with a transparent Hono proxy layer that validates and routes requests without ever exposing the underlying key.</p>
                <div class="border border-neutral-700 overflow-hidden">
                  <img src="/apirecycler.png" alt="LLM Recycler – apirecycler.com" class="w-full h-auto block" loading="lazy" />
                  <div class="px-4 py-2 bg-neutral-900 border-t border-neutral-700 text-xs text-neutral-400">apirecycler.com</div>
                </div>
                <div class="flex flex-wrap gap-1.5">
                  <UBadge v-for="t in ['TypeScript', 'Vue', 'Hono', 'Supabase', 'Stripe', 'Node.js', 'PostgreSQL']" :key="t" :label="t" variant="outline" size="sm" />
                </div>
                <div class="flex gap-2 flex-wrap">
                  <UButton to="https://github.com/elilourens/llmrecycler" target="_blank" icon="i-simple-icons-github" label="GitHub" color="neutral" />
                  <UButton to="https://apirecycler.com" target="_blank" icon="i-lucide-external-link" label="Live site" variant="outline" color="neutral" />
                  <NuxtLink to="/projects/llmrecycler">
                    <UButton label="Full case study" trailing-icon="i-lucide-arrow-right" variant="outline" color="neutral" />
                  </NuxtLink>
                </div>
              </div>
            </template>
          </UModal>

          <!-- SMARTQUERY -->
          <UModal size="xl">
            <div class="min-h-32 md:h-full border border-neutral-800 bg-neutral-950 p-4 cursor-pointer hover:border-yellow-400 hover:bg-white hover:shadow-[3px_3px_0_rgba(250,204,21,0.4)] hover:-translate-x-px hover:-translate-y-px transition-all duration-200 group flex flex-col">
              <div class="flex items-center gap-2 mb-2">
                <UIcon name="i-lucide-search" class="text-yellow-400 size-4 shrink-0" />
                <h3 class="font-bold text-sm text-white group-hover:text-black">SmartQuery</h3>
              </div>
              <p class="text-[11px] text-yellow-400 group-hover:text-black font-semibold mb-1">smartquery.app</p>
              <p class="text-[11px] text-neutral-400 group-hover:text-black leading-relaxed flex-1">Semantic file search: videos, images, text. MCP integration.</p>
              <div class="flex flex-wrap gap-1 mt-3">
                <span v-for="t in ['Python', 'FastAPI', 'Vue', 'Ragie']" :key="t" class="font-mono text-[9px] text-neutral-400 group-hover:text-black border border-neutral-700 px-1.5 py-0.5">{{ t }}</span>
              </div>
              <UIcon name="i-lucide-arrow-up-right" class="size-3 text-neutral-300 mt-2 group-hover:text-yellow-400 transition-colors self-end" />
            </div>
            <template #content>
              <div class="bg-neutral-950 p-6 max-h-[80vh] overflow-y-auto space-y-5">
                <div>
                  <h2 class="text-2xl font-black text-white">SmartQuery</h2>
                  <p class="text-sm text-yellow-400 font-semibold">smartquery.app: Semantic file search</p>
                </div>
                <p class="text-sm text-neutral-300 leading-relaxed">Search your files by their content: videos, images, and text. Find a video by describing a scene. MCP integration and Google Drive sync.</p>
                <div class="flex flex-wrap gap-1.5">
                  <UBadge v-for="t in ['Python', 'FastAPI', 'Vue', 'TypeScript', 'Ragie', 'Docker', 'MCP']" :key="t" :label="t" variant="outline" size="sm" />
                </div>
                <div class="flex gap-2 flex-wrap">
                  <UButton to="https://github.com/elilourens/hypa-thymesia" target="_blank" icon="i-simple-icons-github" label="GitHub" color="neutral" />
                  <UButton to="https://smartquery.app" target="_blank" icon="i-lucide-external-link" label="smartquery.app" variant="outline" color="neutral" />
                  <NuxtLink to="/projects/hypa-thymesia">
                    <UButton label="Full case study" trailing-icon="i-lucide-arrow-right" variant="outline" color="neutral" />
                  </NuxtLink>
                </div>
              </div>
            </template>
          </UModal>

          <!-- STIRBOT -->
          <UModal size="lg">
            <div class="min-h-32 md:h-full border border-neutral-800 bg-neutral-950 p-4 cursor-pointer hover:border-yellow-400 hover:bg-white hover:shadow-[3px_3px_0_rgba(250,204,21,0.4)] hover:-translate-x-px hover:-translate-y-px transition-all duration-200 group flex flex-col">
              <div class="flex items-center gap-2 mb-2">
                <UIcon name="i-lucide-bot" class="text-yellow-400 size-4 shrink-0" />
                <h3 class="font-bold text-sm text-white group-hover:text-black">Stirbot</h3>
              </div>
              <p class="text-[11px] text-yellow-400 group-hover:text-black font-semibold mb-1">University of Stirling</p>
              <p class="text-[11px] text-neutral-400 group-hover:text-black leading-relaxed flex-1">RAG chatbot that scrapes the university website and answers student questions.</p>
              <div class="flex flex-wrap gap-1 mt-3">
                <span v-for="t in ['Python', 'RAG', 'Chatbot']" :key="t" class="font-mono text-[9px] text-neutral-400 group-hover:text-black border border-neutral-700 px-1.5 py-0.5">{{ t }}</span>
              </div>
              <UIcon name="i-lucide-arrow-up-right" class="size-3 text-neutral-300 mt-2 group-hover:text-yellow-400 transition-colors self-end" />
            </div>
            <template #content>
              <div class="bg-neutral-950 p-6 max-h-[80vh] overflow-y-auto space-y-5">
                <div>
                  <h2 class="text-2xl font-black text-white">Stirbot</h2>
                  <p class="text-sm text-yellow-400 font-semibold">University of Stirling AI chatbot</p>
                </div>
                <p class="text-sm text-neutral-300 leading-relaxed">Scrapes the University of Stirling website and answers student questions via a RAG pipeline. Admin mode enables live re-ingestion.</p>
                <div class="flex flex-wrap gap-1.5">
                  <UBadge v-for="t in ['Python', 'Web Scraping', 'RAG', 'Vector Database', 'Gradio', 'NLP']" :key="t" :label="t" variant="outline" size="sm" />
                </div>
                <div class="flex gap-2 flex-wrap">
                  <UButton to="https://github.com/elilourens/stirbot" target="_blank" icon="i-simple-icons-github" label="GitHub" color="neutral" />
                  <NuxtLink to="/projects/stirbot">
                    <UButton label="Full case study" trailing-icon="i-lucide-arrow-right" variant="outline" color="neutral" />
                  </NuxtLink>
                </div>
              </div>
            </template>
          </UModal>

        </div>
      </div>

      <!-- RIGHT: Prophit featured card -->
      <div class="md:w-72 md:shrink-0">
        <UModal size="2xl">
          <div class="min-h-48 md:h-full bg-neutral-950 border border-neutral-800 p-6 cursor-pointer hover:border-yellow-400 hover:shadow-[3px_3px_0_rgba(250,204,21,0.4)] hover:-translate-x-px hover:-translate-y-px transition-all duration-200 group flex flex-col relative overflow-hidden">
            <div class="absolute top-0 left-0 right-0 h-0.5 bg-yellow-400 shimmer-glow"></div>
            <div class="text-[10px] font-mono text-yellow-400 uppercase tracking-widest mt-1 mb-1">🏆 HackEurope 2026</div>
            <div class="text-[10px] text-neutral-500 uppercase tracking-wider mb-4">Monzo Fintech · 1st Place · €1,000</div>
            <h3 class="text-3xl font-black text-white mb-3 tracking-tight">Prophit</h3>
            <p class="text-sm text-neutral-400 leading-relaxed">AI spending prediction app. Analyses past transactions against public datasets to forecast tomorrow's spending. Built in 30 hours, judged by Monzo's CEO. 750+ competitors across Dublin, Paris, Stockholm.</p>
            <div class="flex flex-wrap gap-1 mt-4">
              <span v-for="t in ['React Native', 'TypeScript', 'FastAPI', 'Supabase', 'Solana', 'Claude', 'Gemini']" :key="t" class="font-mono text-[9px] text-neutral-400 border border-neutral-700 px-1.5 py-0.5">{{ t }}</span>
            </div>
            <div class="mt-auto pt-4 flex gap-2">
              <UButton size="sm" label="Details" trailing-icon="i-lucide-arrow-up-right" color="neutral" class="bg-white text-black hover:bg-neutral-100" />
              <UButton size="sm" to="https://github.com/elilourens/prophit" target="_blank" icon="i-simple-icons-github" label="GitHub" variant="outline" color="neutral" class="border-neutral-600 text-white" @click.stop />
            </div>
          </div>
          <template #content>
            <div class="bg-neutral-950 p-6 max-h-[85vh] overflow-y-auto space-y-5">
              <div class="pb-4 border-b border-neutral-800">
                <UBadge label="🏆 HackEurope 2026 Winner · €1,000" size="sm" class="bg-yellow-400 text-black border-0 font-semibold mb-3" />
                <h2 class="text-2xl font-black text-white">Prophit</h2>
                <p class="text-sm text-neutral-400">HackEurope 2026 Winner – Monzo Fintech Track</p>
              </div>
              <p class="text-sm text-neutral-300 leading-relaxed">Built Prophit in 30 hours – a spending prediction app that analyses your past transactions against public datasets (weather, events, calendar) to forecast tomorrow's spending. Judged by Monzo's CEO, Susquehanna, and Red Hat. 750+ competitors across Dublin, Paris, and Stockholm.</p>
              <div class="grid grid-cols-3 gap-px bg-neutral-200 border border-neutral-200">
                <div class="bg-neutral-950 p-4 text-center">
                  <div class="text-2xl font-black text-yellow-400">30h</div>
                  <div class="text-[10px] text-neutral-400 uppercase mt-1">Build time</div>
                </div>
                <div class="bg-neutral-950 p-4 text-center">
                  <div class="text-2xl font-black text-white">750+</div>
                  <div class="text-[10px] text-neutral-400 uppercase mt-1">Competitors</div>
                </div>
                <div class="bg-neutral-950 p-4 text-center">
                  <div class="text-2xl font-black text-white">3</div>
                  <div class="text-[10px] text-neutral-400 uppercase mt-1">Cities</div>
                </div>
              </div>
              <div class="flex flex-wrap gap-1.5">
                <UBadge v-for="t in ['React Native', 'TypeScript', 'FastAPI', 'Supabase', 'Solana', 'Claude', 'Gemini', 'ElevenLabs', 'Stripe']" :key="t" :label="t" variant="outline" size="sm" />
              </div>
              <div class="flex gap-2 flex-wrap">
                <UButton to="https://github.com/elilourens/prophit" target="_blank" icon="i-simple-icons-github" label="View on GitHub" color="neutral" />
                <NuxtLink to="/projects/prophit">
                  <UButton label="Full case study" trailing-icon="i-lucide-arrow-right" variant="outline" color="neutral" />
                </NuxtLink>
              </div>
            </div>
          </template>
        </UModal>
      </div>

    </div>

    <!-- ROW 3: Contact -->
    <div class="grid grid-cols-1 sm:grid-cols-3 gap-2 shrink-0">
      <a href="mailto:elilourens123@gmail.com" class="flex items-center justify-between p-3 border border-neutral-800 bg-neutral-950 hover:border-yellow-400 hover:shadow-[3px_3px_0_rgba(250,204,21,0.4)] hover:-translate-x-px hover:-translate-y-px transition-all duration-200 group">
        <div>
          <div class="text-[9px] text-neutral-400 uppercase tracking-widest font-mono">Email</div>
          <div class="text-sm font-semibold text-white">elilourens123@gmail.com</div>
        </div>
        <UIcon name="i-lucide-arrow-up-right" class="size-4 text-neutral-400 group-hover:text-yellow-400 transition-colors" />
      </a>
      <a href="https://www.linkedin.com/in/eli-lourens/" target="_blank" class="flex items-center justify-between p-3 border border-neutral-800 bg-neutral-950 hover:border-yellow-400 hover:shadow-[3px_3px_0_rgba(250,204,21,0.4)] hover:-translate-x-px hover:-translate-y-px transition-all duration-200 group">
        <div>
          <div class="text-[9px] text-neutral-400 uppercase tracking-widest font-mono">LinkedIn</div>
          <div class="text-sm font-semibold text-white">eli-lourens</div>
        </div>
        <UIcon name="i-lucide-arrow-up-right" class="size-4 text-neutral-400 group-hover:text-yellow-400 transition-colors" />
      </a>
      <a href="https://github.com/elilourens" target="_blank" class="flex items-center justify-between p-3 border border-neutral-800 bg-neutral-950 hover:border-yellow-400 hover:shadow-[3px_3px_0_rgba(250,204,21,0.4)] hover:-translate-x-px hover:-translate-y-px transition-all duration-200 group">
        <div>
          <div class="text-[9px] text-neutral-400 uppercase tracking-widest font-mono">GitHub</div>
          <div class="text-sm font-semibold text-white">elilourens</div>
        </div>
        <UIcon name="i-lucide-arrow-up-right" class="size-4 text-neutral-400 group-hover:text-yellow-400 transition-colors" />
      </a>
    </div>

  </div>
</template>
