<template>
  <div id="center">
    <div id="imgContainer">
      <div id="img" :style="{ backgroundImage: `url(${logo})` }" />
    </div>
  </div>
</template>

<script lang="ts">
import Vue from "vue";

export default Vue.extend({
  name: "CenterTeamFooter",
  components: {},
  props: ["logo"]
});
</script>

<style scoped lang="scss">
#center {
  width: 100%;
  height: 100%;

  display: flex;
  flex: 2 0;
  align-items: center;
  justify-content: center;
  overflow: hidden;
}

#imgContainer {
  width: 100%;
  height: 75%;
  display: flex;
  align-items: center;
  justify-content: center;
}

#img {
  width: 100%;
  height: 100%;
  background-repeat: no-repeat;
  background-size: contain;
  background-position-x: center;
  overflow: hidden;
}
</style>
