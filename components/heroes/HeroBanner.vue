<template>
  <div class="relative py-32 md:py-48 overflow-hidden flex items-center">
    <div v-if="image" class="absolute inset-0 z-0">
      <img :src="image" class="w-full h-full object-cover" />
      <div class="absolute inset-0 bg-black/60"></div>
    </div>

    <UContainer class="relative z-10 w-full">
      <div class="flex flex-col max-w-4xl" :class="alignmentClasses[align]">

        <h1 class="text-4xl font-bold tracking-tight text-white sm:text-6xl">
          {{ title }}
        </h1>

        <p v-if="description" class="mt-6 text-lg text-gray-200 max-w-2xl">
          {{ description }}
        </p>

        <div v-if="buttons" class="mt-10 flex gap-4">
          <UButton
              v-for="(btn, i) in buttons" :key="i"
              :to="btn.to" size="xl" :color="btn.color || 'primary'"
          >
            {{ btn.label }}
          </UButton>
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
  align: {
    type: String,
    default: 'center',
    validator: (value) => ['left', 'center', 'right'].includes(value)
  },
  buttons: Array
})

// Mapping alignment props to Tailwind CSS classes
const alignmentClasses = {
  left: 'text-left items-start',
  center: 'text-center items-center mx-auto',
  right: 'text-right items-end ml-auto'
}
</script>