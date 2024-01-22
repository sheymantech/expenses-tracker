<template>
  <Header />
  <div class="container">
    <balance :total="total" />
    <incomeExpenses :income="income" :expenses="expenses" />
    <transactionList :transactions="transactions" />
    <addTransaction />
  </div>
</template>

<script setup>
import Header from "./components/header.vue";
import balance from "./components/balance.vue";
import incomeExpenses from "./components/income-expenses.vue";
import transactionList from "./components/transaction-list.vue";
import addTransaction from "./components/add-transaction.vue";

import { ref, computed } from "vue";

const transactions = ref([
  { id: 1, text: "sheyi", amount: -34.0 },
  { id: 1, text: "sheyi", amount: 34.0 },
  { id: 1, text: "sheyman", amount: 100.0 },
  { id: 1, text: "sheyi", amount: 34.0 },
]);

const total = computed(() => {
  return transactions.value.reduce((acc, transactions) => {
    return acc + transactions.amount;
  }, 0);
});
const income = computed(() => {
  return transactions.value
    .filter((transactions) => transactions.amount > 0)
    .reduce((acc, transactions) => {
      return acc + transactions.amount;
    }, 0);
});
const expenses = computed(() => {
  return transactions.value
    .filter((transactions) => transactions.amount < 0)
    .reduce((acc, transactions) => {
      return acc + transactions.amount;
    }, 0);
});
</script>
