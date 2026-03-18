<template>
  <div class="max-w-4xl mx-auto px-6 py-10 space-y-10">
    <!-- Header -->
    <div class="flex items-start justify-between gap-6 pb-8 border-b border-neutral-200">
      <div>
        <UBadge label="Python · Web Scraping · RAG · Chatbot" color="neutral" variant="subtle" size="sm" class="mb-3" />
        <h1 class="text-4xl font-black tracking-tight">Stirbot</h1>
        <p class="text-neutral-500 mt-2 leading-relaxed max-w-xl text-sm">A Python chatbot that scrapes and ingests the University of Stirling website, then answers student questions using a RAG pipeline. Two modes: a locked-down tester interface and a full admin panel for re-ingestion.</p>
      </div>
      <div class="flex gap-2 shrink-0">
        <UButton to="/" icon="i-lucide-arrow-left" label="Back" color="neutral" variant="outline" size="sm" />
        <UButton to="https://github.com/elilourens/stirbot" target="_blank" icon="i-simple-icons-github" label="GitHub" color="neutral" size="sm" />
      </div>
    </div>

    <!-- Features grid -->
    <section>
      <h2 class="text-[10px] font-mono text-neutral-400 uppercase tracking-[0.2em] mb-4">Features</h2>
      <div class="grid grid-cols-2 gap-px bg-neutral-950">
        <div v-for="feature in features" :key="feature.title" class="bg-neutral-950 p-5 space-y-3 hover:bg-neutral-900 transition-colors">
          <UIcon :name="feature.icon" class="text-yellow-400 size-5" />
          <h3 class="font-semibold text-sm text-white">{{ feature.title }}</h3>
          <p class="text-xs text-neutral-400 leading-relaxed">{{ feature.description }}</p>
        </div>
      </div>
    </section>

    <!-- Two modes -->
    <section>
      <h2 class="text-[10px] font-mono text-neutral-400 uppercase tracking-[0.2em] mb-4">Two Modes</h2>
      <div class="grid grid-cols-2 gap-px bg-neutral-200 border border-neutral-200">
        <div class="bg-neutral-950 p-5 space-y-2">
          <div class="flex items-center gap-2">
            <UIcon name="i-lucide-message-circle" class="text-yellow-400 size-5 shrink-0" />
            <h3 class="font-semibold text-white">Tester Mode</h3>
          </div>
          <p class="text-sm text-neutral-400 leading-relaxed">The default. Run with <code class="text-xs bg-neutral-800 text-neutral-200 px-1.5 py-0.5 font-mono rounded">python app.py</code> and you get the chatbot interface only – safe for external users and QA testing.</p>
        </div>
        <div class="bg-neutral-950 p-5 space-y-2">
          <div class="flex items-center gap-2">
            <UIcon name="i-lucide-shield" class="text-yellow-400 size-5 shrink-0" />
            <h3 class="font-semibold text-white">Admin Mode</h3>
          </div>
          <p class="text-sm text-neutral-400 leading-relaxed">Run with <code class="text-xs bg-neutral-800 text-neutral-200 px-1.5 py-0.5 font-mono rounded">python app.py --admin</code> to unlock Scrape and Ingest tabs. This replaces the existing database – use with care.</p>
        </div>
      </div>
    </section>

    <!-- Tech Stack -->
    <section>
      <h2 class="text-[10px] font-mono text-neutral-400 uppercase tracking-[0.2em] mb-4">Tech Stack</h2>
      <div class="flex flex-wrap gap-2">
        <UBadge v-for="t in stack" :key="t" :label="t" variant="outline" size="sm" />
      </div>
    </section>

    <!-- CTA -->
    <div class="border border-neutral-800 bg-neutral-950 p-6 flex items-center justify-between gap-6">
      <div>
        <h3 class="font-bold text-white">See the code</h3>
        <p class="text-sm text-neutral-400 mt-1">Stirbot is open source on GitHub.</p>
      </div>
      <div class="flex gap-2 shrink-0">
        <UButton to="https://github.com/elilourens/stirbot" target="_blank" icon="i-simple-icons-github" label="GitHub" color="neutral" class="bg-white text-black hover:bg-neutral-100" />
        <UButton to="/" icon="i-lucide-arrow-left" label="Back to portfolio" variant="outline" color="neutral" class="border-neutral-600 text-white" />
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
useSeoMeta({
  title: 'Stirbot – University Chatbot | Eli Lourens',
  description: 'A RAG-powered chatbot that scrapes the University of Stirling website and answers student questions in natural language.'
})

const features = [
  {
    icon: 'i-lucide-globe',
    title: 'Website Scraper',
    description: 'Crawls the University of Stirling website and extracts text content from pages, feeding it into the ingestion pipeline.'
  },
  {
    icon: 'i-lucide-database',
    title: 'RAG Pipeline',
    description: 'Scraped content is chunked and stored in a vector database. Queries retrieve the most relevant chunks to ground the chatbot\'s responses.'
  },
  {
    icon: 'i-lucide-message-square',
    title: 'Conversational Interface',
    description: 'Students ask questions in plain English and get accurate, source-grounded answers instead of keyword-matched search results.'
  },
  {
    icon: 'i-lucide-refresh-cw',
    title: 'Live Re-ingestion',
    description: 'Admin mode allows authorised users to re-scrape the site and rebuild the database when content is updated.'
  }
]

const stack = ['Python', 'Web Scraping', 'RAG', 'Vector Database', 'Gradio / Streamlit', 'NLP']
</script>
