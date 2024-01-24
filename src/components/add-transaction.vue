<template>
  <h3>Add new transaction</h3>
  <form id="form" @submit.prevent="onSubmit">
    <div class="form-control">
      <label for="text">Text</label>
      <input
        type="text"
        id="text"
        placeholder="Enter text...."
        v-model="text"
      />
    </div>
    <div class="form-control">
      <label for="amount"
        >Amount <br />
        (negative-expenses, positive- income)</label
      >
      <input
        type="number"
        id="amount"
        placeholder="Enter amount...."
        v-model="amount"
      />
    </div>
    <button class="btn">Add transaction</button>
  </form>
</template>

<script setup>
import { ref } from "vue";
import { useToast } from "vue-toastification";
const amount = ref("");
const text = ref("");
const emit = defineEmits(["transactionSubmited"]);
const toast = useToast();
const onSubmit = function () {
  if (!text.value || !amount.value) {
    toast.error("both fields must be filled");
  }
  const transactionData = {
    text: text.value,
    amount: parseFloat(amount.value),
  };
  emit("transactionSubmited", transactionData);
  // console.log(text.value, amount.value);
  text.value = "";
  amount.value = "";
  // console.log(emit);
};
</script>
