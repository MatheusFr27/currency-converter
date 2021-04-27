<template>
  <section class="container-coin">
    <h1>PREÇO DAS MOEDAS</h1>
    <div class="container-coins">
      <!-- Dolar -->
      <div>
        <h2>Dolar</h2>
        <hr />
        <p>$ {{ coins.USDBRL.ask }}</p>
        <router-link
          :to="{
            name: 'Converter',
            params: {
              coin: {
                lang: 'en',
                typeCoin: 'USD',
                nameCoin: 'Dolar',
                coins: coins.USDBRL.ask,
                icon: '$',
              },
            },
          }"
          >Converter Dolar</router-link
        >
      </div>
      <!-- Euro -->
      <div>
        <h2>Euro</h2>
        <hr />
        <p>€ {{ coins.EURBRL.ask }}</p>
        <router-link
          :to="{
            name: 'Converter',
            params: {
              coin: {
                lang: 'eu',
                typeCoin: 'EUR',
                nameCoin: 'Euro',
                coins: coins.EURBRL.ask,
                icon: '€',
              },
            },
          }"
          >Converter Euro</router-link
        >
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data: () => ({
    coins: null,
  }),
  async mounted() {
    // Fazendo requisição da api
    await this.axios
      .get("https://economia.awesomeapi.com.br/last/USD-BRL,EUR-BRL")
      .then((response) => {
        if (response.data.EURBRL && response.data.USDBRL) {
          this.coins = response.data;
        }
      });
  },
};
</script>

<style scoped>
.container-coin {
  width: 100%;

  border-radius: 5px;

  margin: 1em 0;
}

.container-coin h1,
.container-coin .container-coins h2 {
  font-size: 16pt;
  text-align: center;
  color: white;
  cursor: default;

  margin: 0.5em 0;
}

.container-coin .container-coins,
.container-coin .container-coins div {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;

  margin: 1em 0;
}

.container-coin .container-coins {
  background-color: #eeeeee57;
}

.container-coin .container-coins div {
  justify-content: center;
  flex-direction: column;

  border: #f1c40f 2px solid;
  border-radius: 5px;
  padding: 2em;
  margin: 1em 1em;
}

.container-coin .container-coins h2 {
  margin: 0;
}

.container-coin .container-coins hr {
  width: 65%;
  background-color: transparent;
  border: 1px white solid;
}

.container-coin .container-coins p {
  font-family: "Libre Baskerville", serif;
  font-size: 14pt;
  cursor: default;

  color: #2ecc71;

  margin: 0.5em 0;
  margin-bottom: 2em;
}

.container-coin .container-coins a {
  font-family: "Ubuntu", sans-serif;
  font-size: 16pt;

  color: #f3ef20;
  text-decoration: none;

  border: #f3ef20 2px solid;
  padding: 0.2em;
  box-shadow: 0px 0px 12px -2px rgba(224, 224, 25, 1);
}

.container-coin .container-coins a:hover {
  color: #d1bf19;
  border: #d1bf19 2px solid;
}

@media (max-width: 976px) {
  .container-coin .container-coins {
    flex-direction: column;
  }
}
</style>
