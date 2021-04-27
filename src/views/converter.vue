<template>
  <section>
    <h1>
      Convertendo Reais em <strong>{{ calculateCoins.nameCoin }}</strong>
    </h1>

    <!-- Calcular moedas -->
    <div class="container">
      <input v-model="valueOfMoney" type="number" />
      <p>/</p>
      <p class="coins">{{ calculateCoins.coins }}</p>
      <p>=</p>
      <p class="result-price">{{ amount.toFixed(2).replace(".", ",") }}</p>
    </div>
    <button @click="calculateTotal">Calcular</button>
  </section>
</template>

<script>
export default {
  data: () => ({
    calculateCoins: null,
    valueOfMoney: 0,
    amount: 0,
  }),
  methods: {
    calculateTotal: function() {
      return (this.amount = this.valueOfMoney / this.calculateCoins.coins);
    },
  },
  mounted() {
    this.calculateCoins = this.$route.params.coin;
  },
};
</script>

<style scoped>
section {
  height: 100%;
  width: 100%;

  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;

  background-color: rgb(36, 36, 36);
}

section h1 {
  font-size: 16pt;
  color: white;

  margin-bottom: 1em;
}

section strong {
  font-size: 16pt;
  color: rgb(245, 245, 3);
}

.container {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;

  padding: 1em;

  border: white 2px solid;
  border-radius: 5px;
}

.container p {
  color: white;
  margin: 0 1em;
  font-size: 14pt;
}

.container input {
  padding: 0.5em 0.5em;
}

.container .coins {
  font-family: "Libre Baskerville", serif;

  margin: 0;
}

.container .result-price {
  color: rgb(245, 245, 4);
}

section button {
  margin-top: 1em;

  color: white;
  background-color: green;
  padding: 0.5em;

  border-radius: 5px;
  border: none;
}

section button:hover {
  background-color: rgb(0, 145, 0);
  cursor: pointer;
}
</style>
