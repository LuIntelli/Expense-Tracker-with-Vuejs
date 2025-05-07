<template>
  <div class="">
    <h2 class="text-[30px] text-slate-200">History</h2>

    <div class="transactions">
      <div
        v-for="transaction in transactions"
        :key="transaction.id"
        :class="[
          transaction.amount.includes('-')
            ? 'expense  border-red-500'
            : 'income  border-green-500 ',
          ' text-white bg-black border-r-[20px] my-3 pr-3 pl-1 rounded-sm py-3 flex justify-between',
        ]"
      >
        <h4 class="font-bold">{{ transaction.text }}</h4>
        <h4 class="font-bold">{{ transaction.amount }}</h4>
      </div>
    </div>
  </div>
</template>

<script setup>
import { defineProps } from "vue";

const props = defineProps({
  transactions: {
    type: Array,
    required: true,
  },
});
</script>
