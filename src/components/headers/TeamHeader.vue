<template>
  <div id="header">
    <TeamHeaderSide v-bind:team="teamA" :orientation="'leftori'" />
    <CenterTeamHeader id="center" v-bind:center="center" />
    <TeamHeaderSide v-bind:team="teamB" :orientation="'rightori'" />
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import CenterTeamHeader from "./CenterTeamHeader.vue";
import TeamHeaderSide from "./TeamHeaderSide.vue";

export default Vue.extend({
  name: "TeamHeader",
  components: { TeamHeaderSide, CenterTeamHeader },
  props: ["teamA", "teamB", "center"]
});
</script>

<style scoped lang="scss">
#header {
  display: flex;
  height: 100%;
  height: 20vh;

  background-image: url("../../assets/headerbg.png");
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center;
  overflow-y: hidden;
}
</style>
