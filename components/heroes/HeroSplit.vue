<template>
  <div class="py-24 bg-white dark:bg-gray-900">
    <UContainer>
      <div class="grid lg:grid-cols-2 gap-12 items-center">
        <div>
          <h1 class="text-4xl font-bold tracking-tight text-gray-900 dark:text-white sm:text-6xl">
            {{ title }}
          </h1>
          <p class="mt-6 text-lg leading-8 text-gray-600 dark:text-gray-300">
            {{ description }}
          </p>
          <div v-if="buttons" class="mt-10 flex items-center gap-x-6">
            <UButton
                v-for="(btn, i) in buttons"
                :key="i"
                :to="btn.to"
                size="xl"
                :color="btn.color || 'primary'"
            >
              {{ btn.label }}
            </UButton>
          </div>
        </div>

        <div class="relative lg:h-full">
          <img
              v-if="image"
              :src="image"
              class="rounded-2xl shadow-xl ring-1 ring-gray-900/10 w-full object-cover"
              alt="Hero image"
          />
        </div>
      </div>
    </UContainer>
  </div>
</template>

<script setup>

//Props
const props = defineProps({
  title: String,
  description: String,
  image: String,
  buttons: Array
})
</script>