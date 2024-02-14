<script setup>
import { ref } from "vue";
import DataTable from "../components/DataTable.vue";

function getRandomPrice(min, max) {
  return (Math.random() * (max - min) + min).toFixed(2);
}

const items = ref([
  {
    id: 13,
    assigned: "Alice Johnson",
    status: "completed",
    title: "Project Alpha",
    price: getRandomPrice(10, 100),
    details: "Details for Project 32",
  },
  {
    id: 14,
    assigned: "Bob Smith",
    status: "started",
    title: "Task Beta",
    price: getRandomPrice(10, 100),
    details: "Details for Project 32",
  },
  {
    id: 15,
    assigned: "Charlie Brown",
    status: "completed",
    title: "Mission Gamma",
    price: getRandomPrice(10, 100),
    details: "Details for Project 32",
  },
  {
    id: 16,
    assigned: "David Miller",
    status: "started",
    title: "Objective Delta",
    price: getRandomPrice(10, 100),
    details: "Details for Project 32",
  },
  {
    id: 17,
    assigned: "Eva White",
    status: "completed",
    title: "Assignment Epsilon",
    price: getRandomPrice(10, 100),
    details: "Details for Project 32",
  },
  {
    id: 18,
    assigned: "Frank Wilson",
    status: "started",
    title: "Operation Zeta",
    price: getRandomPrice(10, 100),
    details: "Details for Project 32",
  },
  {
    id: 19,
    assigned: "Grace Harris",
    status: "completed",
    title: "Task Eta",
    price: getRandomPrice(10, 100),
    details: "Details for Project 32",
  },
  {
    id: 20,
    assigned: "Henry Davis",
    status: "started",
    title: "Mission Theta",
     price: getRandomPrice(10, 100),
    details: "Details for Project 32",
  },
  {
    id: 21,
    assigned: "Ivy Jones",
    status: "completed",
    title: "Project Iota",
     price: getRandomPrice(10, 100),
    details: "Details for Project 32",
  },
  {
    id: 22,
    assigned: "Jack Brown",
    status: "started",
    title: "Task Kappa",
    price: getRandomPrice(10, 100),
    details: "Details for Project 32",
  },
  {
    id: 23,
    assigned: "Karen Taylor",
    status: "completed",
    title: "Objective Lambda",
    price: getRandomPrice(10, 100),
    details: "Details for Project 32",
  },
  {
    id: 24,
    assigned: "Leo Miller",
    status: "started",
    title: "Assignment Mu",
    price: getRandomPrice(10, 100),
    details: "Details for Project 32",
  },
  {
    id: 25,
    assigned: "Mia Wilson",
    status: "completed",
    title: "Operation Nu",
    price: getRandomPrice(10, 100),
    details: "Details for Project 32",
  },
  {
    id: 26,
    assigned: "Nathan Harris",
    status: "started",
    title: "Task Xi",
    price: getRandomPrice(10, 100),
    details: "Details for Project 32",
  },
  {
    id: 27,
    assigned: "Olivia Davis",
    status: "completed",
    title: "Mission Omicron",
    price: getRandomPrice(10, 100),
    details: "Details for Project 32",
  },
  {
    id: 28,
    assigned: "Paul White",
    status: "started",
    title: "Project Pi",
    price: getRandomPrice(10, 100),
    details: "Details for Project 32",
  },
  {
    id: 29,
    assigned: "Quinn Taylor",
    status: "completed",
    title: "Task Rho",
    price: getRandomPrice(10, 100),
    details: "Details for Project 32",
  },
  {
    id: 30,
    assigned: "Ryan Miller",
    status: "started",
    title: "Objective Sigma",
    price: getRandomPrice(10, 100),
    details: "Details for Project 32",
  },
  {
    id: 31,
    assigned: "Samantha Wilson",
    status: "completed",
    title: "Assignment Tau",
    price: getRandomPrice(10, 100),
    details: "Details for Project 32",
  },
  {
    id: 32,
    assigned: "Zoe Turner",
    status: "started",
    title: "Operation Omega",
    price: getRandomPrice(10, 100),
    details: "Details for Project 32",
  },
]);
</script>

<template>
  <div class="p-8 bg-gray-100 min-h-screen">
    <DataTable :items="items" />
  </div>
</template>
