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
  /* height: 100%;
  box-shadow: inset 0 -8px 0 $black-1; */
  background-color: $gray-1;
}

a {
  text-decoration-line: none;
}
</style>
