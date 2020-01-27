<template>
  <div id="center">
    <ChampionList v-bind:team="picks.teamA" :orientation="'left'" />
    <CenterSpace />
    <ChampionList v-bind:team="picks.teamB" :orientation="'right'" />
  </div>
</template>

<script lang="ts">
import Vue from "vue";

import ChampionList from "./ChampionList.vue";
import CenterSpace from "./CenterSpace.vue";

export default Vue.extend({
  name: "CenterContainer",
  components: { ChampionList, CenterSpace },
  props: ["picks"]
});
</script>

<style scoped lang="scss"></style>
