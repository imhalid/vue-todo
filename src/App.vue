<template>
  <div
    class="h-[650px] w-96 bg-neutral-200 rounded-3xl shadow-lg border-2 px-5 border-gray-400 overflow-hidden"
  >
    <Title :title="title" />
    <div>
      <input
        type="text"
        class="w-full flex h-10 px-3 rounded-md outline-none focus:ring-0 mt-5"
        placeholder="add item"
        @keyup.enter="addData($event)"
        :value="data.title"
      />
    </div>
    <div class="h-full overflow-auto scroll-smooth">
      <div
        v-for="(item, index) in data"
        :key="index"
        class="w-auto h-20 flex place-items-center justify-between bg-neutral-300 mt-5 rounded-lg"
      >
        <div class="mx-3 flex items-center">
          <button @click="toggleComplete(item)">
            <div class="w-5 h-5 rounded-full border-2 border-black relative">
              <div
                class="bg-gradient-to-tr from-emerald-500 to bg-emerald-600 w-3 h-3 transition-all rounded-full absolute top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2"
                :class="{ 'scale-0': !item.complete }"
              ></div>
            </div>
          </button>
        </div>
        <div class="flex-1 text-left text-neutral-900">
          {{ item.title }}
        </div>
        <div class="aspect-square h-10 flex items-center justify-center">
          <button @click="deleteData">
            <DeleteIcon class="h-7 w-7 text-rose-500" />
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import DeleteIcon from '@/icons/DeleteIcon.vue'
import { ref } from 'vue'
import Title from './components/Title.vue'

const data = ref([])
const title = 'Content'

const toggleComplete = event => {
  event.complete = !event.complete
}

const addData = event => {
  data.value.push({
    id: new Date().getTime(),
    title: event.target.value,
    complete: false,
  })
}
const deleteData = event => {
  data.value.splice(event, 1)
}
</script>
