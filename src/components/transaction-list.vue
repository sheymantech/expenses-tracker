<template>
  <h3>History</h3>
  <ul id="list " class="list">
    <li
      v-for="transaction in transactions"
      :key="transaction.id"
      :class="transaction.amount < 0 ? 'minus' : 'plus'"
    >
      {{ transaction.text }} <span>{{ transaction.amount }}</span>
      <button class="delete-btn" @click="deleteTransaction(transaction.id)">
        x
      </button>
    </li>
    <!-- <li class="minus">
      cash <span>-$400</span>
      <button class="delete-btn">x</button>
    </li>
    <li class="plus">
      Paycheck <span>$800</span>
      <button class="delete-btn">x</button>
    </li> -->
  </ul>
</template>

<script setup>
import { defineProps } from "vue";
const props = defineProps({
  transactions: {
    type: Array,
    required: true,
  },
});
const emit = defineEmits(["transactionDeleted"]);
//delete transaction

const deleteTransaction = (id) => {
  emit("transactionDeleted", id);
};
</script>
