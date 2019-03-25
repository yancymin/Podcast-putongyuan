<template>
  <div id="app">
    <router-view/>
  </div>
</template>

<style lang="scss">
@import "./style/reset.css";
@import "./style/global.scss";

#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: $black-1;
  display: flex;
  justify-content: center;
}

:root {
  background-color: $gray-1;
}

a {
  text-decoration-line: none;
}
</style>
