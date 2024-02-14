<script setup>
import { ref, computed } from "vue";

const show = ref(false);

const props = defineProps({
  items: {
    type: Array,
    required: true,
  },
});

const emit = defineEmits(["filter"]);

const statuses = computed(() => {
  return [...new Set(props.items.map((item) => item.status))];
});

const filter = (e) => {
  emit("filter", e.target.value);
};
</script>

<template>
  <div class="relative flex items-center w-full px-4">
    <button
      @click="show = !show"
      class="w-full flex items-center justify-center py-2 px-4 text-sm font-medium text-gray-700"
    >
      Filter
    </button>
    <div
      v-if="show"
      class="absolute px-3 top-12 right-0 z-10 w-28 bg-white rounded-md shadow"
    >
      <h6 class="mb-2 mt-2 text-sm font-medium text-gray-700">Status</h6>
      <ul class="space-y-2 text-sm">
        <li v-for="(status, index) in statuses" :key="index">
          <input
            :id="`filter_option_${index}`"
            @change="filter"
            type="checkbox"
            :value="status"
            class="w-4 h-4"
          />
          <label
            :for="`filter_option_${index}`"
            class="ml-2 text-sm font-medium"
            >{{ status }}</label
          >
        </li>
      </ul>
    </div>
  </div>
</template>
