<template>
  <div class="head">
    <p><a href="https://en.wikipedia.org/wiki/Sonification">Сонификация</a> - метод перобразоования измеряемых данных в
      звуковые колебания. </p>
    <p>Все материалы взяты из открытых источников Wiki и NASA</p>
  </div>
  <router-view />
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}
</style>
