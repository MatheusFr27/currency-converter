<template>
  <section class="home">
    <h1>Conversor de Moeda</h1>
    <coinDisplay />
  </section>
</template>

<script>
// @ is an alias to /src
import coinDisplay from "../components/coinDisplay";

export default {
  name: "Home",
  components: {
    coinDisplay,
  },
};
</script>

<style scoped>
.home {
  height: 100%;
  width: 100%;

  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;

  background-image: url("../assets/img/background-dolar.jpg");
  background-position: center;
  background-attachment: scroll;
  background-repeat: repeat;
  background-size: cover;

  animation: movimentImageBackground 15s infinite alternate ease;
}

.home h1 {
  font-size: 25pt;
  color: white;
  text-align: center;

  margin-top: 1em;
}

@keyframes movimentImageBackground {
  0% {
    /* background-position-x: 0%; */

    background-size: 100%;
  }
  100% {
    /* background-position-x: -700%; */

    background-size: 200%;
  }
}
</style>
