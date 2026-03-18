<script setup>
useHead({
  meta: [
    { name: 'viewport', content: 'width=device-width, initial-scale=1' }
  ],
  link: [
    { rel: 'icon', href: '/favicon.ico' },
    { rel: 'preconnect', href: 'https://fonts.googleapis.com' },
    { rel: 'preconnect', href: 'https://fonts.gstatic.com', crossorigin: '' },
    { rel: 'stylesheet', href: 'https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@300;400;500;600;700&display=swap' }
  ],
  htmlAttrs: { lang: 'en' }
})

useSeoMeta({
  title: 'Eli Lourens – Developer',
  description: 'Final-year CS student, AI engineer, and HackEurope 2026 winner. Building AI-powered applications.',
  ogTitle: 'Eli Lourens – Developer',
  ogDescription: 'Final-year CS student, AI engineer, and HackEurope 2026 winner.',
  twitterCard: 'summary_large_image'
})

const navLinks = [
  { label: 'About', to: '#about' },
  { label: 'Experience', to: '#experience' },
  { label: 'Startups', to: '#startups' },
  { label: 'Projects', to: '#projects' },
  { label: 'Contact', to: '#contact' }
]
</script>

<template>
  <UApp class="md:flex md:flex-col md:h-screen">
    <UHeader>
      <template #left>
        <NuxtLink to="/" class="font-semibold text-base tracking-tight">
          Eli Lourens
        </NuxtLink>
      </template>

      <template #body>
        <UNavigationMenu :links="navLinks" />
      </template>

      <template #right>
        <UButton
          to="https://github.com/elilourens"
          target="_blank"
          icon="i-simple-icons-github"
          aria-label="GitHub"
          color="neutral"
          variant="ghost"
        />
        <UButton
          to="https://www.linkedin.com/in/eli-lourens/"
          target="_blank"
          icon="i-simple-icons-linkedin"
          aria-label="LinkedIn"
          color="neutral"
          variant="ghost"
        />
      </template>
    </UHeader>

    <UMain class="md:flex-1 md:overflow-hidden md:min-h-0 md:h-full">
      <NuxtPage />
    </UMain>
  </UApp>
</template>
