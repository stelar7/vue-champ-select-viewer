<template>
  <div :id="orientation" class="parent">
    <div id="imageContainer">
      <img :src="getImage()" id="image" />
    </div>
    <div id="coach" v-if="team.coach">Coach: {{ team.coach }}</div>
    <div id="team">{{ team.name }}</div>
  </div>
</template>

<script lang="ts">
import Vue from "vue";

export default Vue.extend({
  name: "LeftTeamHeader",
  components: {},
  props: ["team", "orientation"],
  methods: {
    getImage() {
      return require("../../" + this.team.logo);
    }
  }
});
</script>

<style scoped lang="scss">
#leftori {
  flex-direction: row;

  #imageContainer {
    flex-direction: row;
  }

  #coach {
    left: 1%;
  }

  #team {
    // padding-left: 20%;
  }
}

#rightori {
  flex-direction: row-reverse;

  #imageContainer {
    flex-direction: row-reverse;
  }

  #coach {
    right: 1%;
  }

  #team {
    // padding-right: 20%;
  }
}

#leftori,
#rightori {
  // box-shadow: inset 25px -20px 25px 0px rgba(0, 0, 0, 0.75);
  // background-color: #112;
  display: flex;
  overflow: hidden;
  position: relative;
  width: 100%;
  height: 100%;
  flex: 2 0;
}

#imageContainer {
  width: 100%;
  height: 100%;
  position: relative;
  top: -10%;
  display: flex;
}

#image {
  height: 150%;
  filter: opacity(0.5);
}

#coach {
  position: absolute;
  bottom: 1%;
  font-size: 1.25em;
  text-shadow: 2px 2px #333;
}

#team {
  font-weight: 1000;
  font-size: 2.5em;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  width: 100%;
  height: 100%;
}
</style>
