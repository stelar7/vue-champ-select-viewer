<template>
  <div id="list">
    <PlayerCard v-for="player in team" v-bind:key="player.player" :player="player" :orientation="orientation" />
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import PlayerCard from "./PlayerCard.vue";

export default Vue.extend({
  name: "ChampionList",
  components: { PlayerCard },
  props: ["orientation", "team"]
});
</script>

<style scoped lang="scss">
#list {
  display: flex;
  flex-direction: column;
  justify-content: space-evenly !important;
  text-align: center;
  align-items: center;
  height: 100%;
  flex: 1 0;
  background: rgba(34, 34, 34, 0.1);
}
</style>
