<template>
  <h2 class="mt-10 mb-3 border-b pb-2 border-slate-800">Add new transaction</h2>
  <div class="">
    <form action="#" @submit.prevent="AddTransactionData" class="w-full py-5">
      <div class="text">
        <label for="text">Text</label>
        <input
          type="text"
          name="text"
          v-model="transactionData.text"
          id="text"
          placeholder="Add Product name"
          class="bg-black block w-full my-4 px-4 rounded text-white py-4 border border-slate-800 outline-none"
        />
      </div>
      <div class="amount">
        <label for="amount" class="block">Amount</label>
        <span> ( negative - expense, positive - income ) </span>
        <input
          type="text"
          name="amount"
          id="amount"
          placeholder="Add Price"
          v-model="transactionData.amount"
          class="bg-black block w-full mb-4 mt-2 rounded text-white p-4 border border-slate-800 outline-none"
        />
      </div>
      <button type="submit" class="rounded bg-blue-800 p-4 w-full block">
        Add Transaction
      </button>
    </form>
  </div>
</template>

<script setup>
import { reactive } from "vue";
import { useToast } from "vue-toastification";

const toast = useToast();
const transactionData = reactive({
  text: "",
  amount: "",
});

// Send this data to the parent component, to update every other component.
// In Vue, to “emit” means to send a custom event from a child component to the parent, optionally passing data with it.

const emit = defineEmits(["transactionDataSubmitted"]);

const AddTransactionData = () => {
  // Validation of the input boxes
  if (transactionData.text === "" || transactionData.amount === "") {
    toast.error("Both fields must be filled");
  } else {
    emit("transactionDataSubmitted", transactionData);
    transactionData.text = "";
    transactionData.amount = "";
  }

  // console.log(transactions.text, transactions.amount);
};
</script>
