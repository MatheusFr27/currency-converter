<template>
  <section>
    <h1>
      Convertendo Reais em <strong>{{ calculateCoins.nameCoin }}</strong>
    </h1>

    <!-- Calcular moedas -->
    <div class="container-base">
      <div class="container">
        <input
          accesskey="k"
          title="Alt + k para poder selecionar o input de calculo"
          v-model="valueOfMoney"
          type="number"
        />
        <p>÷</p>
        <p class="coins">
          {{ calculateCoins.icon }} {{ calculateCoins.coins }}
        </p>
      </div>

      <p class="equal">=</p>
      <p class="result-price">
        {{ calculateCoins.icon }}
        {{
          amount.toFixed(2).toLocaleString(calculateCoins.lang, {
            style: "currency",
            currency: calculateCoins.typeCoin,
          })
        }}
      </p>
    </div>

    <div class="container-base">
      <!-- Para voltar a página inicial -->
      <router-link class="return-home" to="/">Retornar ao Home</router-link>
      <!-- Botão de calcular -->
      <button
        accesskey="j"
        title="Alt + j para poder selecionar o botão de calcular"
        @click="calculateTotal"
      >
        Calcular
      </button>
    </div>
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
      let value = parseInt(this.valueOfMoney);
      return (this.amount = value / this.calculateCoins.coins);
    },
  },
  mounted() {
    if (
      this.$route.params.coin.coins &&
      this.$route.params.coin.nameCoin &&
      this.$route.params.coin.icon
    ) {
      this.calculateCoins = this.$route.params.coin;
    } else {
      this.$router.push("/");
    }
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
  font-size: 18pt;
  color: white;

  margin-bottom: 1em;
}

section strong {
  font-size: 16pt;
  color: rgb(245, 245, 3);
}

.container-base .container {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;

  padding: 1em;

  border: white 2px solid;
  border-radius: 5px;
}

.container-base .container p {
  color: white;
  margin: 0 1em;
  font-size: 14pt;
}

.container-base .container input {
  padding: 0.5em 0.5em;
  width: 7em;
}

.container-base .container .coins {
  font-family: "Libre Baskerville", serif;

  margin: 0;
}

.container-base .equal {
  color: white;
  margin: 0em 1em;
}

.container-base .result-price {
  color: rgb(245, 245, 4);
  font-size: 14pt;
  background-color: rgb(85, 85, 85);
  padding: 0.2em;
  border-radius: 5px;
}

.container-base {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
}

section button,
.container-base .return-home {
  margin: 1em 0.5em 0em 0.5em;

  color: white;
  font-size: 14pt;
  background-color: green;
  padding: 0.5em 1em;

  border-radius: 5px;
  border: none;
}

.container-base .return-home {
  background-color: rgb(233, 55, 42);
  text-decoration: none;
}

.container-base .return-home:hover {
  background-color: rgb(236, 72, 60);
}

section button:hover {
  background-color: rgb(0, 145, 0);
  cursor: pointer;
}
</style>
