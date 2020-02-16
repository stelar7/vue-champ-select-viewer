<template>
  <div id="center"></div>
</template>

<script lang="ts">
import Vue from "vue";

export default Vue.extend({
  name: "CenterSpace",
  components: {},
  props: []
});
</script>

<style scoped lang="scss">
#center {
  display: flex;
  height: 100%;
  width: 100%;
  background: rgba(0, 255, 0, 1);
  flex-direction: row;
  flex: 3 0;
}
</style>
