<template>
  <div id="center">
    <div id="top">
      <img :src="center.logo" id="centerImg" />
    </div>
    <div id="bottom">
      <div id="timerA" v-if="center.teamA.phaseTimer > 0">{{ center.teamA.phaseTimer }}</div>
      <div id="timerA" v-else></div>
      <div id="score">
        <div id="scoreA">{{ center.teamA.score }}</div>
        <div>-</div>
        <div id="scoreB">{{ center.teamB.score }}</div>
      </div>
      <div id="timerB" v-if="center.teamB.phaseTimer > 0">{{ center.teamB.phaseTimer }}</div>
      <div id="timerB" v-else></div>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from "vue";

export default Vue.extend({
  name: "CenterTeamHeader",
  components: {},
  props: ["center"]
});
</script>

<style scoped lang="scss">
#center {
  height: 100%;
  background: rgba(0, 0, 0, 0.6);
  box-shadow: 0px 0px 25px 25px rgba(0, 0, 0, 0.5);

  display: flex;
  flex-direction: column;
  flex: 1 1;

  justify-content: flex-start;

  font-size: 2em;
  text-align: center;
  align-items: center;
  justify-content: flex-start;
}

#top {
  padding-top: 10%;
  min-height: 20%;
  width: 50%;
  display: flex;
  flex-direction: row;

  justify-content: center;
}

#centerImg {
  display: flex;
  width: 50%;
  padding-bottom: 5%;
}

#bottom {
  width: 100%;
  display: flex;
  flex-direction: row;
  justify-content: space-around;

  padding-top: 10%;

  text-align: center;
  align-items: center;
}

#score {
  display: flex;
  width: 40%;
  flex-direction: row;

  text-align: center;
  align-items: center;
  justify-content: space-evenly;
}

#timerA,
#timerB {
  width: 20%;
  text-align: center;
  align-items: center;
  padding: 1% 0;
}
</style>
