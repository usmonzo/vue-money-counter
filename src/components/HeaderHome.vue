<template>
  <header>
    <h1>Money Tracker</h1>
    <div class="total-income">{{ totalIncome }}₽</div>
  </header>
</template>

<script>
export default {
  props: {
    totalIncome: Number,
  },
};
</script>

<style scoped>
header {
  justify-self: center;

  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 15px 30px;

  background-color: #101010;
  border-bottom: 5px solid #3523d6;
}
header h1 {
  color: #eee;
  font-size: 28px;
}
header .total-income {
  font-family: "Fira Code", "Fira Sans", sans-serif;
  background-color: #3523d6;
  color: #fff;
  font-size: 20px;
  font-weight: 900;
  padding: 5px;
  min-width: 90px;
  text-align: center;
  border-radius: 8px;
  box-shadow: inset 0px 0px 6px rgba(0, 0, 0, 0.25);
  text-shadow: 0px 3px 3px rgba(0, 0, 0, 0.25);
}
</style>
