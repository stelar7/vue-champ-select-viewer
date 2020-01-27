<template>
  <AppBase />
</template>

<script lang="ts">
import Vue from "vue";
import AppBase from "./components/AppBase.vue";

export default Vue.extend({
  name: "app",
  components: {
    AppBase
  }
});
</script>

<style lang="scss">
@import "../node_modules/css-reset-and-normalize/scss/reset-and-normalize";
@import "../node_modules/css-reset-and-normalize/scss/button-reset";
@import "../node_modules/css-reset-and-normalize/scss/link-reset";
@import url("https://fonts.googleapis.com/css?family=Roboto&display=swap");

html body {
  font-family: Roboto, Calibri, Helvetica, Arial, sans-serif !important;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: wheat;
  background-color: black;
  height: 100vh;
  width: 100vw;
}
</style>
