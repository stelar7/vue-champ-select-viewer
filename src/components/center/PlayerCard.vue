<template>
  <div class="player" :id="orientation">
    <div id="spells">
      <div class="spell" :style="{ backgroundImage: `url(${spellAUrl()})` }" />
      <div class="spell" :style="{ backgroundImage: `url(${spellBUrl()})` }" />
    </div>

    <div id="name" :style="{ backgroundImage: `url(${backgroundUrl()})` }">
      {{ player.name }}
    </div>
  </div>
</template>

<script lang="ts">
import Vue from "vue";

export default Vue.extend({
  name: "PlayerCard",
  components: {},
  props: ["player", "orientation"],
  methods: {
    spellAUrl() {
      return require("@/assets/spells/" + this.player.spell1Id + ".png");
    },
    spellBUrl() {
      return require("@/assets/spells/" + this.player.spell2Id + ".png");
    },
    backgroundUrl() {
      let skin = (this.player.skin + "").padStart(6, "0");
      skin = skin.substring(0, 3).padEnd(6, "0");
      return require("@/assets/splash/" + skin + ".png");
    }
  }
});
</script>

<style scoped lang="scss">
.player {
  width: 100%;
  height: 100%;
  max-height: 115px;
  display: flex;
  flex-direction: row;
  align-items: center;
  position: relative;
}

#left {
  #spells {
    position: absolute;
    height: 100%;
    width: 100%;

    display: flex;
    flex-direction: column;
    justify-content: space-evenly;
    align-items: flex-start;
    padding: 0 0 0 3%;
  }
  .spell {
    border: 2px solid #333;
    width: 40px;
    height: 40px;

    display: flex;
    justify-content: center;
    align-items: center;
    background-repeat: no-repeat;
    background-size: cover;
  }
  #name {
    height: 100%;
    width: 100%;
    font-size: 1.4em;
    text-shadow: 2px 2px #333;

    display: flex;
    align-items: flex-end;
    flex-direction: row-reverse;
    padding: 0 2% 2% 0;

    background-repeat: no-repeat;
    background-size: cover;
  }
}

#right {
  flex-direction: row-reverse;

  #spells {
    position: absolute;
    height: 100%;
    width: 100%;

    display: flex;
    flex-direction: column;
    justify-content: space-evenly;
    align-items: flex-end;
    padding: 0 3% 0 0;
  }
  .spell {
    border: 2px solid #333;
    width: 40px;
    height: 40px;

    display: flex;
    justify-content: center;
    align-items: center;
    background-repeat: no-repeat;
    background-size: cover;
  }
  #name {
    height: 100%;
    width: 100%;
    font-size: 1.4em;
    text-shadow: 2px 2px #333;

    display: flex;
    align-items: flex-end;
    flex-direction: row;
    padding: 0 0 2% 2%;

    background-repeat: no-repeat;
    background-size: cover;
  }
}
</style>
