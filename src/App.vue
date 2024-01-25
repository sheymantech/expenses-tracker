<template>
  <Header />
  <div class="container">
    <balance :total="total" />
    <incomeExpenses :income="income" :expenses="expenses" />
    <transactionList
      :transactions="transactions"
      @transactionDeleted="handleTransactionDeleted"
    />
    <addTransaction @transactionSubmited="handleTransactionSubmited" />
  </div>
</template>

<script setup>
import Header from "./components/header.vue";
import balance from "./components/balance.vue";
import incomeExpenses from "./components/income-expenses.vue";
import transactionList from "./components/transaction-list.vue";
import addTransaction from "./components/add-transaction.vue";

import { ref, computed, onMounted } from "vue";
import { useToast } from "vue-toastification";
const toast = useToast();

const transactions = ref([]);
onMounted(() => {
  const savedTransactions = JSON.parse(localStorage.getItem("transactions"));
  if (savedTransactions) {
    transactions.value = savedTransactions;
  }
});

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
//Add transaction
const handleTransactionSubmited = (transactionData) => {
  transactions.value.push({
    id: generateUniqueId(),
    text: transactionData.text,
    amount: transactionData.amount,
  });
  saveTransactionsToLocalStorage();
  toast.success("transaction added successfully ");
};

console.log(transactions);
console.log(generateUniqueId());
const generateUniqueId = () => {
  return Math.floor(Math.random() * 1000000);
};

// delete transaction
const handleTransactionDeleted = (id) => {
  transactions.value = transactions.value.filter(
    (transaction) => transaction.id !== id
  );
  saveTransactionsToLocalStorage();
  toast.success("transaction deleted");
};
// save transaction to local storage
const saveTransactionsToLocalStorage = () => {
  localStorage.setItem("transactions", JSON.stringify(transactions.value));
};
</script>
