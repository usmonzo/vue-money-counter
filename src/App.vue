<template>
  <HeaderHome :totalIncome="state.totalIncome" />
  <FormHome @add-income="AddIncome" />
  <IncomeList :state="state" />
</template>

<script>
import { reactive, computed } from "vue";
import HeaderHome from "./components/HeaderHome";
import FormHome from "./components/FormHome.vue";
import IncomeList from "./components/IncomeList.vue";

export default {
  setup() {
    const state = reactive({
      income: [],
      sortedIncome: computed(() => {
        let temp = [];

        temp = state.income.forEach(function (a, b) {
          return b.date - a.date;
        });
        return temp;
      }),
      totalIncome: computed(() => {
        let temp = 0;

        if (state.income.length > 0) {
          for (let i = 0; i < state.income.length; i++) {
            temp += state.income[i].value;
          }
        }
        return temp;
      }),
    });
    function AddIncome(data) {
      let d = data.date.split("-");
      let newD = new Date(d[0], d[1], d[2]);

      state.income = [
        ...state.income,
        {
          id: Date.now(),
          desc: data.desc,
          value: parseInt(data.value),
          date: newD.getTime(),
        },
      ];
      console.log(state.income);
    }

    return {
      state,
      AddIncome,
    };
  },

  components: {
    HeaderHome,
    FormHome,
    IncomeList,
  },
};
</script>
<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Fira Sans", sans-serif;
}
body {
  background: #eee;
}
</style>
