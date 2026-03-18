<template>
  <div class="max-w-4xl mx-auto px-6 py-10 space-y-10">
    <!-- Header -->
    <div class="flex items-start justify-between gap-6 pb-8 border-b border-neutral-200">
      <div>
        <UBadge label="Live at smartquery.app" class="bg-yellow-400 text-black border-0 font-semibold mb-3" size="sm" />
        <h1 class="text-4xl font-black tracking-tight">SmartQuery</h1>
        <p class="text-neutral-500 mt-2 leading-relaxed max-w-xl text-sm">Search your files by their content – not their name. SmartQuery understands videos, images, and text files. Find a video by describing a scene, ask questions about your documents, and give your AI tools access to your entire file library.</p>
      </div>
      <div class="flex gap-2 shrink-0">
        <UButton to="/" icon="i-lucide-arrow-left" label="Back" color="neutral" variant="outline" size="sm" />
        <UButton to="https://smartquery.app" target="_blank" icon="i-lucide-external-link" label="Live" color="neutral" size="sm" />
        <UButton to="https://github.com/elilourens/hypa-thymesia" target="_blank" icon="i-simple-icons-github" label="GitHub" color="neutral" variant="outline" size="sm" />
      </div>
    </div>

    <!-- What is it -->
    <section>
      <h2 class="text-[10px] font-mono text-neutral-400 uppercase tracking-[0.2em] mb-4">What is SmartQuery?</h2>
      <p class="text-sm text-neutral-600 leading-relaxed">Most file search tools match on filenames and metadata. SmartQuery indexes the actual content – so you can describe what you're looking for in plain language and find it, even across thousands of files.</p>
    </section>

    <!-- Features grid -->
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

    <!-- Architecture -->
    <section>
      <h2 class="text-[10px] font-mono text-neutral-400 uppercase tracking-[0.2em] mb-4">Architecture</h2>
      <div class="space-y-3 text-sm text-neutral-600 leading-relaxed">
        <p>The project is split into two services: a <strong class="text-neutral-900">Python FastAPI backend</strong> that handles file ingestion, semantic embedding, and search via Ragie, and a <strong class="text-neutral-900">Vue + TypeScript frontend</strong> that provides the search interface and Google Drive integration.</p>
        <p>Docker Compose orchestrates both services for local development. The backend also exposes a <strong class="text-neutral-900">Model Context Protocol (MCP)</strong> server, letting AI assistants like Claude query your files directly as a tool during conversations.</p>
        <p>140 commits and counting – deployed live at <a href="https://smartquery.app" target="_blank" class="text-yellow-600 underline underline-offset-2">smartquery.app</a>.</p>
      </div>
    </section>

    <!-- Tech Stack -->
    <section>
      <h2 class="text-[10px] font-mono text-neutral-400 uppercase tracking-[0.2em] mb-4">Tech Stack</h2>
      <div class="grid grid-cols-2 gap-8">
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
      </div>
    </section>

    <!-- CTA -->
    <div class="border border-neutral-800 bg-neutral-950 p-6 flex items-center justify-between gap-6">
      <div>
        <h3 class="font-bold text-white">Try it live</h3>
        <p class="text-sm text-neutral-400 mt-1">SmartQuery is live at smartquery.app and open source under the MIT licence.</p>
      </div>
      <div class="flex gap-2 shrink-0">
        <UButton to="https://smartquery.app" target="_blank" icon="i-lucide-external-link" label="smartquery.app" color="neutral" class="bg-white text-black hover:bg-neutral-100" />
        <UButton to="https://github.com/elilourens/hypa-thymesia" target="_blank" icon="i-simple-icons-github" label="GitHub" variant="outline" color="neutral" class="border-neutral-600 text-white" />
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
useSeoMeta({
  title: 'SmartQuery – Semantic File Search | Eli Lourens',
  description: 'Search your files by content – videos, images, and text. Live at smartquery.app.'
})

const features = [
  {
    icon: 'i-lucide-search',
    title: 'Semantic Search',
    description: 'Search by meaning, not filename. Ask "meeting notes from last quarter" or "photo of the team dinner" and get the right file.'
  },
  {
    icon: 'i-lucide-video',
    title: 'Video Scene Search',
    description: 'Describe a scene – "a dog jumping over a puddle" – and SmartQuery finds the exact moment across your video library.'
  },
  {
    icon: 'i-lucide-image',
    title: 'Image & Text Files',
    description: 'Indexes images, PDFs, documents, and text files. One search bar for your entire local file system.'
  },
  {
    icon: 'i-lucide-cpu',
    title: 'MCP Integration',
    description: 'Give your AI assistant access to your files as a tool. Claude, Cursor, and other MCP-compatible clients can query SmartQuery directly.'
  },
  {
    icon: 'i-simple-icons-googledrive',
    title: 'Google Drive Sync',
    description: 'Connect your Google Drive and search cloud files alongside local ones – everything in one place.'
  },
  {
    icon: 'i-lucide-box',
    title: 'Docker Compose',
    description: 'Both services start with a single command for local development or self-hosting.'
  }
]

const backendStack = ['Python', 'FastAPI', 'Uvicorn', 'Ragie', 'MCP', 'Poetry', 'Docker']
const frontendStack = ['Vue 3', 'TypeScript', 'Vite']
</script>
