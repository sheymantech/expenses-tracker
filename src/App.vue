<template>
  <Header />
  <div class="container">
    <balance />
    <incomeExpenses />
    <transactionList />
    <addTransaction />
  </div>
</template>

<script>
import Header from "./components/header.vue";
import balance from "./components/balance.vue";
import incomeExpenses from "./components/income-expenses.vue";
import transactionList from "./components/transaction-list.vue";
import addTransaction from "./components/add-transaction.vue";
export default {
  components: {
    Header,
    balance,
    incomeExpenses,
    transactionList,
    addTransaction,
  },
};
</script>
