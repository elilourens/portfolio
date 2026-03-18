<template>
  <div class="max-w-4xl mx-auto px-6 py-10 space-y-10">

    <!-- Header -->
    <div class="flex items-start justify-between gap-6 pb-8 border-b border-neutral-200">
      <div>
        <div class="flex items-center gap-2 mb-3">
          <UBadge label="TypeScript · Vue · Hono · Supabase · Stripe" color="neutral" variant="subtle" size="sm" />
        </div>
        <h1 class="text-4xl font-black tracking-tight">LLM Recycler</h1>
        <p class="text-neutral-500 mt-2 leading-relaxed max-w-xl text-sm">A marketplace for LLM API keys. Buy, sell, and proxy unused AI API credits so nothing goes to waste. Stripe payments, Supabase backend, and a Hono proxy layer – all wrapped in a Vue frontend.</p>
      </div>
      <div class="flex gap-2 shrink-0">
        <UButton to="/" icon="i-lucide-arrow-left" label="Back" color="neutral" variant="outline" size="sm" />
        <UButton to="https://github.com/elilourens/llmrecycler" target="_blank" icon="i-simple-icons-github" label="GitHub" color="neutral" size="sm" />
        <UButton to="https://apirecycler.com" target="_blank" icon="i-lucide-external-link" label="Live" color="neutral" variant="outline" size="sm" />
      </div>
    </div>

    <!-- What is it -->
    <section>
      <h2 class="text-[10px] font-mono text-neutral-400 uppercase tracking-[0.2em] mb-4">What is LLM Recycler?</h2>
      <p class="text-sm text-neutral-600 leading-relaxed">Developers often accumulate API credits they'll never use – leftover from trials, cancelled subscriptions, or project pivots. LLM Recycler is a peer-to-peer marketplace where those credits can be listed, purchased, and used via a transparent proxy layer.</p>
    </section>

    <!-- Features grid -->
    <section>
      <h2 class="text-[10px] font-mono text-neutral-400 uppercase tracking-[0.2em] mb-4">Features</h2>
      <div class="grid grid-cols-3 gap-px bg-neutral-950">
        <div v-for="feature in features" :key="feature.title" class="bg-neutral-950 p-5 space-y-3 hover:bg-neutral-900 transition-colors">
          <UIcon :name="feature.icon" class="text-yellow-400 size-5" />
          <h3 class="font-semibold text-sm text-white">{{ feature.title }}</h3>
          <p class="text-xs text-neutral-400 leading-relaxed">{{ feature.description }}</p>
        </div>
      </div>
    </section>

    <!-- Architecture -->
    <section>
      <h2 class="text-[10px] font-mono text-neutral-400 uppercase tracking-[0.2em] mb-4">Architecture</h2>
      <div class="space-y-3 text-sm text-neutral-600 leading-relaxed">
        <p>The backend is a <strong class="text-neutral-900">Hono API</strong> running on Node.js with six core route groups: key management, buyer keys, a proxy service, user profiles, Stripe payment webhooks, and pricing. Supabase handles both authentication and the Postgres database.</p>
        <p>The proxy endpoint is the heart of the product – it intercepts requests from buyers, swaps in the seller's API key, and forwards the call to the upstream LLM provider. This means buyers never see the actual key, and usage is tracked transparently.</p>
        <p>The frontend is a <strong class="text-neutral-900">Vue 3 + TypeScript</strong> SPA (44% each) with a test site for verifying proxy behaviour end-to-end.</p>
      </div>
    </section>

    <!-- Screenshot -->
    <section>
      <h2 class="text-[10px] font-mono text-neutral-400 uppercase tracking-[0.2em] mb-4">Screenshot</h2>
      <div class="border border-neutral-200 overflow-hidden">
        <img src="/apirecycler.png" alt="LLM Recycler, apirecycler.com" class="w-full h-auto block" loading="lazy" />
        <div class="px-4 py-2 bg-neutral-50 border-t border-neutral-200 text-xs text-neutral-400">apirecycler.com</div>
      </div>
    </section>

    <!-- Tech Stack -->
    <section>
      <h2 class="text-[10px] font-mono text-neutral-400 uppercase tracking-[0.2em] mb-4">Tech Stack</h2>
      <div class="grid grid-cols-3 gap-8">
        <div>
          <h3 class="text-xs font-semibold text-neutral-400 uppercase tracking-widest mb-3">Backend</h3>
          <div class="flex flex-wrap gap-2">
            <UBadge v-for="t in backendStack" :key="t" :label="t" variant="outline" size="sm" />
          </div>
        </div>
        <div>
          <h3 class="text-xs font-semibold text-neutral-400 uppercase tracking-widest mb-3">Frontend</h3>
          <div class="flex flex-wrap gap-2">
            <UBadge v-for="t in frontendStack" :key="t" :label="t" variant="outline" size="sm" />
          </div>
        </div>
        <div>
          <h3 class="text-xs font-semibold text-neutral-400 uppercase tracking-widest mb-3">Infrastructure</h3>
          <div class="flex flex-wrap gap-2">
            <UBadge v-for="t in infraStack" :key="t" :label="t" variant="outline" size="sm" />
          </div>
        </div>
      </div>
    </section>

    <!-- CTA -->
    <div class="border border-neutral-800 bg-neutral-950 p-6 flex items-center justify-between gap-6">
      <div>
        <h3 class="font-bold text-white">See the code</h3>
        <p class="text-sm text-neutral-400 mt-1">LLM Recycler is open source under the MIT licence.</p>
      </div>
      <div class="flex gap-2 shrink-0">
        <UButton to="https://github.com/elilourens/llmrecycler" target="_blank" icon="i-simple-icons-github" label="GitHub" color="neutral" class="bg-white text-black hover:bg-neutral-100" />
        <UButton to="/" icon="i-lucide-arrow-left" label="Back to portfolio" variant="outline" color="neutral" class="border-neutral-600 text-white" />
      </div>
    </div>

  </div>
</template>

<script setup lang="ts">
useSeoMeta({
  title: 'LLM Recycler | Eli Lourens',
  description: 'A marketplace for buying and selling LLM API keys, built with TypeScript, Vue, Hono, Supabase, and Stripe.'
})

const features = [
  {
    icon: 'i-lucide-key',
    title: 'API Key Marketplace',
    description: 'Sellers list unused API keys with pricing. Buyers purchase access and consume credits through the platform\'s proxy – keys stay private throughout.'
  },
  {
    icon: 'i-lucide-shuffle',
    title: 'Transparent Proxy',
    description: 'A dedicated proxy endpoint intercepts buyer requests, injects the seller\'s key, and forwards calls to the upstream LLM provider with usage tracking.'
  },
  {
    icon: 'i-lucide-credit-card',
    title: 'Stripe Payments',
    description: 'Fully integrated Stripe checkout and webhook handling. Payments are processed securely and trigger key access grants in real time.'
  },
  {
    icon: 'i-lucide-user',
    title: 'Auth & Profiles',
    description: 'Supabase email-password authentication with user profile management. Separate buyer and seller roles with appropriate API access.'
  },
  {
    icon: 'i-lucide-bar-chart-2',
    title: 'Pricing Engine',
    description: 'A dedicated pricing route gives buyers transparent cost estimates before purchase, factoring in key type and remaining credits.'
  },
  {
    icon: 'i-lucide-flask-conical',
    title: 'Test Site',
    description: 'A built-in test site lets developers verify proxy behaviour and key validity end-to-end before going live.'
  }
]

const backendStack = ['TypeScript', 'Hono', 'Node.js']
const frontendStack = ['Vue 3', 'TypeScript', 'HTML']
const infraStack = ['Supabase', 'PostgreSQL', 'Stripe']
</script>
