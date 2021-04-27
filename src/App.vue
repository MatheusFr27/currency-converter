<template>
  <div id="app">
    <router-view />
  </div>
</template>

<style>
@import url("https://fonts.googleapis.com/css2?family=Ubuntu&display=swap"); /* font-family: 'Ubuntu', sans-serif; */
@import url("https://fonts.googleapis.com/css2?family=Libre+Baskerville&display=swap"); /* font-family: 'Libre Baskerville', serif; */

* {
  margin: 0;
  padding: 0;
  font-size: 12pt;
}

html,
body {
  height: 100%;
  width: 100%;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;

  height: 100%;
  width: 100%;

  display: flex;
  justify-content: center;
  align-items: center;
}

@media (max-width: 975px) {
  html,
  body {
    height: auto;
  }
}
</style>
