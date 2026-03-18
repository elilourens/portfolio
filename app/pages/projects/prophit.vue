<template>
  <div class="max-w-4xl mx-auto px-6 py-10 space-y-10">

    <!-- Header -->
    <div class="flex items-start justify-between gap-6 pb-8 border-b border-neutral-200">
      <div>
        <div class="flex items-center gap-2 mb-3">
          <UBadge label="🏆 HackEurope 2026 · 1st Place · €1,000 · Monzo Fintech Track" class="bg-yellow-400 text-black border-0 font-semibold" size="sm" />
        </div>
        <h1 class="text-4xl font-black tracking-tight">Prophit</h1>
        <p class="text-neutral-500 mt-2 leading-relaxed max-w-xl text-sm">A spending prediction app built in 30 hours at HackEurope 2026. Won 1st place and €1,000 in the Monzo Fintech track. Predicts tomorrow's spending by analysing past transactions against public datasets: weather, local events, holidays, calendar.</p>
      </div>
      <div class="flex gap-2 shrink-0">
        <UButton to="/" icon="i-lucide-arrow-left" label="Back" color="neutral" variant="outline" size="sm" />
        <UButton to="https://github.com/elilourens/prophit" target="_blank" icon="i-simple-icons-github" label="GitHub" color="neutral" size="sm" />
      </div>
    </div>

    <!-- Stats -->
    <div class="grid grid-cols-3 gap-px bg-neutral-200 border border-neutral-200">
      <div class="bg-neutral-950 p-6 text-center">
        <div class="text-4xl font-black text-yellow-400">30h</div>
        <div class="text-[10px] text-neutral-400 uppercase tracking-widest mt-2">Build time</div>
      </div>
      <div class="bg-neutral-950 p-6 text-center">
        <div class="text-4xl font-black text-white">750+</div>
        <div class="text-[10px] text-neutral-400 uppercase tracking-widest mt-2">Competitors</div>
      </div>
      <div class="bg-neutral-950 p-6 text-center">
        <div class="text-4xl font-black text-white">3</div>
        <div class="text-[10px] text-neutral-400 uppercase tracking-widest mt-2">Dublin · Paris · Stockholm</div>
      </div>
    </div>

    <!-- Context -->
    <section>
      <h2 class="text-[10px] font-mono text-neutral-400 uppercase tracking-[0.2em] mb-4">HackEurope 2026</h2>
      <div class="space-y-3 text-sm text-neutral-600 leading-relaxed">
        <p>HackEurope is Europe's largest student hackathon, running simultaneously across three cities – Dublin, Paris, and Stockholm. In February 2026, <strong class="text-neutral-900">750+ programmers</strong> competed in a 30-hour overnight sprint.</p>
        <p>Prophit was built entirely during those 30 hours and awarded <strong class="text-neutral-900">1st place and €1,000 in the Monzo Fintech track</strong>. The judges included <strong class="text-neutral-900">Monzo's CEO, Susquehanna, and Red Hat</strong>.</p>
      </div>
      <figure class="mt-6 border border-neutral-200 overflow-hidden">
        <img src="/hackeurope.jpeg" alt="HackEurope 2026 – Dublin" class="w-full object-cover" />
        <figcaption class="px-4 py-2 bg-neutral-50 border-t border-neutral-200 text-xs text-neutral-400">HackEurope 2026 – Dublin</figcaption>
      </figure>
    </section>

    <!-- Features -->
    <section>
      <h2 class="text-[10px] font-mono text-neutral-400 uppercase tracking-[0.2em] mb-4">Features</h2>
      <div class="grid grid-cols-3 gap-px bg-neutral-950">
        <div v-for="(feature, index) in features" :key="feature.title" class="bg-neutral-950 p-5 space-y-3 hover:bg-neutral-900 transition-colors">
          <div class="text-3xl font-black text-white/10 leading-none">{{ String(index + 1).padStart(2, '0') }}</div>
          <div class="flex items-center gap-2">
            <UIcon :name="feature.icon" class="text-yellow-400 size-5 shrink-0" />
            <h3 class="font-semibold text-sm text-white">{{ feature.title }}</h3>
          </div>
          <p class="text-xs text-neutral-400 leading-relaxed">{{ feature.description }}</p>
        </div>
      </div>
    </section>

    <!-- Tech Stack -->
    <section>
      <h2 class="text-[10px] font-mono text-neutral-400 uppercase tracking-[0.2em] mb-4">Tech Stack</h2>
      <div class="grid grid-cols-2 gap-8">
        <div>
          <h3 class="text-xs font-semibold text-neutral-400 uppercase tracking-widest mb-3">Frontend</h3>
          <div class="flex flex-wrap gap-2">
            <UBadge v-for="t in frontendStack" :key="t" :label="t" variant="outline" size="sm" />
          </div>
        </div>
        <div>
          <h3 class="text-xs font-semibold text-neutral-400 uppercase tracking-widest mb-3">Backend & AI</h3>
          <div class="flex flex-wrap gap-2">
            <UBadge v-for="t in backendStack" :key="t" :label="t" variant="outline" size="sm" />
          </div>
        </div>
        <div>
          <h3 class="text-xs font-semibold text-neutral-400 uppercase tracking-widest mb-3">Data & Auth</h3>
          <div class="flex flex-wrap gap-2">
            <UBadge v-for="t in dataStack" :key="t" :label="t" variant="outline" size="sm" />
          </div>
        </div>
        <div>
          <h3 class="text-xs font-semibold text-neutral-400 uppercase tracking-widest mb-3">Blockchain & Payments</h3>
          <div class="flex flex-wrap gap-2">
            <UBadge v-for="t in blockchainStack" :key="t" :label="t" variant="outline" size="sm" />
          </div>
        </div>
      </div>
    </section>

    <!-- CTA -->
    <div class="border border-neutral-800 bg-neutral-950 p-6 flex items-center justify-between gap-6">
      <div>
        <h3 class="font-bold text-white">See the code</h3>
        <p class="text-sm text-neutral-400 mt-1">Prophit is open source. Browse the full React Native + FastAPI codebase on GitHub.</p>
      </div>
      <div class="flex gap-2 shrink-0">
        <UButton to="https://github.com/elilourens/prophit" target="_blank" icon="i-simple-icons-github" label="GitHub" color="neutral" class="bg-white text-black hover:bg-neutral-100" />
        <UButton to="/" icon="i-lucide-arrow-left" label="Back to portfolio" variant="outline" color="neutral" class="border-neutral-600 text-white" />
      </div>
    </div>

  </div>
</template>

<script setup lang="ts">
useSeoMeta({
  title: 'Prophit – HackEurope 2026 Winner | Eli Lourens',
  description: 'Spending prediction app that won 1st place (€1,000) in the Monzo Fintech track at HackEurope 2026. Judged by Monzo\'s CEO, Susquehanna, and Red Hat.'
})

const features = [
  {
    icon: 'i-lucide-brain',
    title: 'Multi-LLM Consensus',
    description: 'Claude Haiku, Gemini 2.5 Flash, and GPT-4o Mini analyse transactions in parallel. Their outputs are synthesised into a single spending forecast calendar.'
  },
  {
    icon: 'i-lucide-mic',
    title: 'Voice Briefings',
    description: 'Every morning, ElevenLabs reads out your weather, top spending predictions, and gentle financial nudges. Voice input powered by Groq Whisper.'
  },
  {
    icon: 'i-lucide-trophy',
    title: 'Blockchain Savings Arena',
    description: 'Compete with friends in savings challenges backed by Solana escrow. Three modes: Budget Guardian, Vice Streak, and Savings Sprint.'
  },
  {
    icon: 'i-lucide-trending-up',
    title: 'Spending Forecasts',
    description: 'Weather-responsive daily predictions with probability indicators. See how long your savings will last and simulate life changes like job transitions.'
  },
  {
    icon: 'i-lucide-message-circle',
    title: 'AI Financial Assistant',
    description: 'Chat with "The Prophit" – Groq\'s Llama 3.3-70B – for contextual financial advice grounded in your actual spending history.'
  },
  {
    icon: 'i-lucide-credit-card',
    title: 'Premium Tier',
    description: 'Stripe-powered Pro subscription (€1.99/month) unlocks full history, scenario simulation, and all voice and AI features.'
  }
]

const frontendStack = ['React Native', 'Expo SDK 54', 'TypeScript', 'Expo Router', 'react-native-chart-kit']
const backendStack = ['Python', 'FastAPI', 'Vercel', 'Claude Haiku 4.5', 'Gemini 2.5 Flash', 'GPT-4o Mini', 'Groq Llama 3.3-70B', 'ElevenLabs']
const dataStack = ['Supabase', 'PostgreSQL', 'AsyncStorage']
const blockchainStack = ['Solana', '@solana/web3.js', 'Devnet', 'Stripe']
</script>
