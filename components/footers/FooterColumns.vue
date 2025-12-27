<script setup>
defineProps({
  companyName: String,
  description: String,
  columns: Array
})

const currentYear = new Date().getFullYear()
</script>

<template>
  <footer class="bg-gray-50 dark:bg-gray-900" aria-labelledby="footer-heading">
    <h2 id="footer-heading" class="sr-only">Footer</h2>

    <UContainer class="pt-16 pb-8">
      <div class="xl:grid xl:grid-cols-3 xl:gap-8">

        <div class="space-y-4 mb-8 xl:mb-0">
          <span class="text-2xl font-bold text-gray-900 dark:text-white">{{ companyName }}</span>
          <p v-if="description" class="text-sm leading-6 text-gray-600 dark:text-gray-400 max-w-xs">
            {{ description }}
          </p>
        </div>

        <div class="grid grid-cols-2 gap-8 xl:col-span-2">
          <div v-for="(col, index) in columns" :key="index" class="md:grid md:gap-8">
            <div>
              <h3 class="text-sm font-semibold leading-6 text-gray-900 dark:text-white">
                {{ col.title }}
              </h3>
              <ul role="list" class="mt-6 space-y-4">
                <li v-for="(link, l) in col.links" :key="l">
                  <NuxtLink
                      :to="link.to"
                      class="text-sm leading-6 text-gray-600 hover:text-primary-500 dark:text-gray-400 dark:hover:text-white transition-colors"
                  >
                    {{ link.label }}
                  </NuxtLink>
                </li>
              </ul>
            </div>
          </div>
        </div>
      </div>

      <div class="mt-16 border-t border-gray-900/10 dark:border-white/10 pt-8 sm:mt-20 lg:mt-24">
        <p class="text-xs leading-5 text-gray-500 text-center">
          &copy; {{ currentYear }} {{ companyName }}. Powered by AI Web Agency.
        </p>
      </div>
    </UContainer>
  </footer>
</template>