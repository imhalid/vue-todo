<template>
  <p class="text-neutral-900 font-extrabold text-5xl text-left mt-5 ml-5">
    {{ props.title }}
  </p>
</template>

<script setup>
const props = defineProps({
  title: {
    type: String,
    required: true,
  },
})
</script>
