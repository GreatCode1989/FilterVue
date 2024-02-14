<script setup>
import { computed, ref } from "vue";
import FilterDropdown from "./FilterDropdown.vue";
import FilterRadios from "./FilterRadios.vue";
import SearchForm from "./SearchForm.vue";

const searchFilter = ref("");
const radioFilter = ref("");
const checkboxFilter = ref([]);

const props = defineProps({
  items: {
    type: Array,
    required: true,
  },
});

const filteredItems = computed(() => {
  let items = [...props.items]; // Создаем копию массива

  switch (radioFilter.value) {
    case "today":
      items = items.sort((a, b) => {
        const priceA = parseFloat(a.price);
        const priceB = parseFloat(b.price);

        return priceA - priceB;
      });
      break;
    case "past":
      items = items.sort((a, b) => {
        const priceA = parseFloat(a.price);
        const priceB = parseFloat(b.price);

        return priceB - priceA;
      });
      break;
  }

  if (checkboxFilter.value.length) {
    items = items.filter((item) => checkboxFilter.value.includes(item.status));
  }

  const searchLowerCase = searchFilter.value.toLowerCase();

  if (searchLowerCase !== "") {
    items = items.filter(
      (item) =>
        item.title.toLowerCase().includes(searchLowerCase) ||
        item.assigned.toLowerCase().includes(searchLowerCase)
    );
  }

  return items;
});


const handleSearch = (search) => {
  searchFilter.value = search;
};

const handleRadioFilter = (filter) => {
  radioFilter.value.push(filter);
};

const handleCheckboxFilter = (filter) => {
  if (checkboxFilter.value.includes(filter)) {
    return checkboxFilter.value.splice(checkboxFilter.value.indexOf(filter), 1);
  }
  return (checkboxFilter.value = filter);
};
</script>

<template>
  <div class="bg-white relative border rounded-lg">
    <div class="flex items-center justify-between">
      <SearchForm @search="handleSearch" />
      <div class="flex items-center justify-end text-sm font-semibold">
        <FilterRadios @filter="handleRadioFilter" />
        <FilterDropdown :items="items" @filter="handleCheckboxFilter" />
      </div>
    </div>
    <table class="w-full text-sm text-left text-gray-500">
      <thead class="text-xs text-gray-700 uppercase bg-gray-50">
        <tr>
          <th class="px-4 py-3">ID</th>
          <th class="px-4 py-3">Assigned To</th>
          <th class="px-4 py-3">Status</th>
          <th class="px-4 py-3">Title</th>
          <th class="px-4 py-3">Price</th>
          <th class="px-4 py-3"><span class="sr-only">Actions</span></th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in filteredItems" :key="item.id" class="border-b">
          <td class="px-4 py-3 font-medium text-gray-700">{{ item.id }}</td>
          <td class="px-4 py-3 font-medium text-gray-700">
            {{ item.assigned }}
          </td>
          <td class="px-4 py-3">{{ item.status }}</td>
          <td class="px-4 py-3">{{ item.title }}</td>
          <td class="px-4 py-3">{{ item.price }}</td>
          <td class="px-4 py-3 flex items-center justify-end">
            <a href="#" class="text-indigo-500 hover:underline">Details</a>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>
