<template>
  <Header />
  <div class="container">
    <balance />
    <incomeExpenses />
    <transactionList />
  </div>
</template>

<script>
import Header from "./components/header.vue";
import balance from "./components/balance.vue";
import incomeExpenses from "./components/income-expenses.vue";
import transactionList from "./components/transaction-list.vue";
export default {
  components: {
    Header,
    balance,
    incomeExpenses,
    transactionList,
  },
};
</script>
