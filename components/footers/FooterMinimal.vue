<script setup>
defineProps({
  companyName: String,
  socialLinks: Array
})

const currentYear = new Date().getFullYear()
</script>

<template>
  <footer class="bg-white dark:bg-gray-900 border-t border-gray-200 dark:border-gray-800">
    <UContainer class="py-8 flex flex-col md:flex-row md:items-center md:justify-between gap-4">

      <div class="text-center md:text-left text-sm text-gray-500 dark:text-gray-400">
        <span class="font-bold text-gray-900 dark:text-white">{{ companyName }}</span>
        <span class="ml-2">&copy; {{ currentYear }}. All rights reserved.</span>
      </div>

      <div v-if="socialLinks && socialLinks.length" class="flex justify-center gap-2">
        <UButton
            v-for="(social, i) in socialLinks"
            :key="i"
            :icon="social.icon"
            :to="social.to"
            target="_blank"
            color="gray"
            variant="ghost"
            size="sm"
        />
      </div>

    </UContainer>
  </footer>
</template>