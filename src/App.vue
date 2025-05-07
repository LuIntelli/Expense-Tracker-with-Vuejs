<template>
  <div class="bg-black">
    <div class="text-white p-5 text-center">
      <Top />
    </div>
    <div
      class="bg-black text-white mx-auto md:w-[50%] border-t p-4 border-slate-800"
    >
      <Balance :balance = "balance" />
      <Record />
      <History />
      <AddTransaction />
    </div>
  </div>
</template>

<script setup>
import Top from "./components/Header.vue";
import Balance from "./components/Balance.vue";
import Record from "./components/Record.vue";
import History from "./components/History.vue";
import AddTransaction from "./components/AddTransaction.vue";

import { ref, computed } from "vue";

const transactions = ref([
  {
    text: "Bought Phone",
    amount: "-280000",
  },
  {
    text: "Bought Phone",
    amount: "-280000",
  },
  {
    text: "Sold Phone",
    amount: "280000",
  },
]);

// Calculate Balance
const balance = computed(() => {
  return transactions.value.reduce((acc, transaction) => {
    return acc + +transaction.amount
  }, 0).toFixed(2);
})



</script>
