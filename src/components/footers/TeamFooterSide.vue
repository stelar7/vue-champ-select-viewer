<template>
  <div :id="orientation" class="tfscommon">
    <div v-for="champion in bans" :key="champion" id="banParent">
      <div class="champion" :style="{ backgroundImage: `url(${getImageLocked(champion)})` }"></div>
      <!-- <div class="champion" :style="{ backgroundImage: `url(${getImage(champion)})` }"></div> -->
      <!-- <div class="banIcon" :style="{ backgroundImage: `url(${getBanImage()})` }"></div> -->
    </div>
  </div>
</template>

<script lang="ts">
import Vue from "vue";

export default Vue.extend({
  name: "RightTeamFooter",
  components: {},
  props: ["bans", "orientation"],
  methods: {
    /*
    getImage(id: string): string {
      return require("@/assets/banHover/" + id + ".png");
    },
    getBanImage(): string {
      return require("@/assets/banOverlay.png");
    }
    */
    getImageLocked(id: string): string {
      return require("@/assets/banLocked/" + id + ".png");
    }
  }
});
</script>

<style scoped lang="scss">
.tfscommon {
  width: 100%;
  height: 100%;
  display: flex;
  flex: 2 0;
  align-items: center;
  justify-content: space-evenly;
}

#right {
  flex-direction: row-reverse;
}

#left {
  flex-direction: row;
}

.champion {
  display: flex;
  width: 75px;
  height: 75px;

  position: absolute;

  background: transparent;
  background-repeat: no-repeat;
  background-size: cover;
}
.banIcon {
  width: 75px;
  height: 75px;

  position: relative;

  background-repeat: no-repeat;
  background-size: cover;
}

#banParent {
  display: flex;
  flex-direction: column;

  align-items: center;
  justify-content: space-evenly;
}
</style>
