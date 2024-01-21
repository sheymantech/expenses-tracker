<template>
  <h3>History</h3>
  <ul id="list " class="list">
    <li
      v-for="transaction in transactions"
      :key="transaction.id"
      :class="transaction.amount < 0 ? 'minus' : 'plus'"
    >
      {{ transaction.text }} <span>{{ transaction.amount }}</span>
      <button class="delete-btn">x</button>
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

<script>
export default {
  data() {
    return {
      transactions: [
        { id: 1, text: "sheyi", amount: -34.0 },
        { id: 1, text: "sheyi", amount: -34.0 },
        { id: 1, text: "sheyman", amount: 100.0 },
        { id: 1, text: "sheyi", amount: -34.0 },
      ],
    };
  },
};
</script>
