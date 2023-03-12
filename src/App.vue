<template>
  <div
    class="h-[650px] w-96 bg-neutral-200 rounded-3xl shadow-lg border-2 border-gray-400"
  >
    <p class="text-neutral-900 font-extrabold text-5xl text-left mt-5 ml-5">
      Header
    </p>
    <div
      class="w-auto h-20 flex place-items-center justify-between bg-neutral-300 mx-5 mt-5 rounded-lg"
    >
      <div class="mx-3 flex items-center">
        <button @click="toggleComplete">
          <div class="w-5 h-5 rounded-full border-2 border-black relative">
            <div
              class="bg-gradient-to-tr from-emerald-500 to bg-emerald-600 w-3 h-3 transition-all rounded-full absolute top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2"
              :class="{ 'scale-0': !complete }"
            ></div>
          </div>
        </button>
      </div>
      <div class="flex-1 text-left text-neutral-900">Hello Word, from Vue</div>
      <div class="aspect-square h-10 flex items-center justify-center">
        <button>
          <DeleteIcon class="h-7 w-7 text-rose-500" />
        </button>
      </div>
    </div>
  </div>
</template>

<script setup>
import DeleteIcon from '@/icons/DeleteIcon.vue'
import { ref, watch } from 'vue'

let complete = ref(false)

const toggleComplete = () => {
  complete.value = !complete.value
}

watch(() => {
  console.log(complete.value)
})
</script>
