<template>
  <div class="bg-black">
    <div class="text-white p-5 text-center">
      <Top />
    </div>
    <div
      class="bg-black text-white mx-auto md:w-[50%] border-t p-4 border-slate-800"
    >
      <Balance :balance="balance" />
      <Record :income="+income" :expense="+expense" />
      <History :transactions="transactions" />
      <AddTransaction @transactionDataSubmitted="handleAddTransactionData" />
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
import { useToast } from "vue-toastification";

const toast = useToast();

const transactions = ref([
  {
    id: 1,
    text: "Bought Phone",
    amount: "-280000",
  },
  {
    id: 2,

    text: "Bought Phone",
    amount: "-280000",
  },
  {
    id: 3,

    text: "Sold Phone",
    amount: "280000",
  },
]);

// Calculate Balance
const balance = computed(() => {
  return transactions.value
    .reduce((acc, transaction) => {
      return acc + +transaction.amount;
    }, 0)
    .toFixed(2);
});

// Calculate the Income
const income = computed(() => {
  return transactions.value
    .filter((transaction) => !transaction.amount.includes("-"))
    .reduce((acc, transaction) => {
      return acc + +transaction.amount;
    }, 0)
    .toFixed(2);
});

// Calculate the Expense
const expense = computed(() => {
  return transactions.value
    .filter((transaction) => transaction.amount.includes("-"))
    .reduce((acc, transaction) => {
      return acc + +transaction.amount;
    }, 0)
    .toFixed(2);
});


// Handling Transaction Data
const handleAddTransactionData = (transactionData) => {
  transactions.value.push({
    id:transactions.length + 1,
    ...transactionData
  })
  toast.success("Transaction Data Added")
}
</script>
