<script setup>
const emit = defineEmits(['search'])

const search = (e) => {
emit('search', e.target.value)
}
</script>  

<template>
  <form class="py-3 px-4 flex items-center">
    <label class="sr-only">Search</label>
    <div class="relative w-full">
      <input
        type="text"
        placeholder="Search"
        @input="search"
        class="bg-gray-50 border border-gray-300 text-gray-900 px-4 py-1.5 rounded-xl focus:ring focus:ring-blue-500 focus:bg-white"
      />
    </div>
  </form>
</template>
