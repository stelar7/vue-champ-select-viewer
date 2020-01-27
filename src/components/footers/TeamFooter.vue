<template>
  <div id="footer">
    <TeamFooterSide id="left" :bans="teamA" :orientation="'left'" />
    <CenterTeamFooter id="center" :logo="center.logo" />
    <TeamFooterSide id="right" :bans="teamB" :orientation="'right'" />
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import CenterTeamFooter from "./CenterTeamFooter.vue";
import TeamFooterSide from "./TeamFooterSide.vue";

export default Vue.extend({
  name: "TeamFooter",
  components: { TeamFooterSide, CenterTeamFooter },
  props: ["teamA", "teamB", "center"]
});
</script>

<style scoped lang="scss">
#footer {
  display: flex;
  height: 100%;
  width: 100%;
  height: 20vh;
  background: linear-gradient(90deg, rgba(0, 0, 0, 0) 0%, rgba(25, 25, 25, 1) 40%, rgba(25, 25, 25, 1) 60%, rgba(0, 0, 0, 0) 100%);
}
</style>
