<template>
  <h2 class="text-slate-300 font-medium text-[30px]">Your Balance</h2>
  <h1 class="text-slate-300 font-medium bg-blue-900 p-3 rounded text-[30px]">${{ balance }}</h1>
</template>

<script setup>
    import { defineProps } from "vue";

    defineProps({
        balance: {
            type: Number,
            required:true
        }
    })

</script>