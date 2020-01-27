<template>
  <div id="container">
    <TeamHeader :teamA="header.teamA" :teamB="header.teamB" :center="header.center" id="header" />
    <CenterContainer v-bind:picks="picks" id="center" />
    <TeamFooter :teamA="bans.teamA" :teamB="bans.teamB" :center="bans.center" id="footer" />
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import TeamHeader from "./headers/TeamHeader.vue";
import CenterContainer from "./center/CenterContainer.vue";
import TeamFooter from "./footers/TeamFooter.vue";

export default Vue.extend({
  name: "AppBase",
  components: {
    TeamHeader,
    CenterContainer,
    TeamFooter
  },
  data: function() {
    return {
      header: {
        teamA: {
          name: "FNATIC",
          coach: "Dylan Falco",
          logo: "assets/teams/fnatic.png"
        },
        teamB: {
          name: "TSM",
          coach: "Parth",
          logo: "assets/teams/tsm.png"
        },
        center: {
          teamA: {
            score: 1,
            phaseTimer: 0
          },
          teamB: {
            score: 1,
            phaseTimer: 0
          },
          logo: "https://upload.wikimedia.org/wikipedia/en/d/df/Riot_Games_%282019%29.svg"
        }
      },
      bans: {
        teamA: [15, 245, 64, 497, 114],
        teamB: [17, 80, 61, 222, 5],
        center: {
          logo: "https://upload.wikimedia.org/wikipedia/en/d/df/Riot_Games_%282019%29.svg"
        }
      },
      picks: {
        teamA: [
          { uuid: 0, team: 1, skin: "001000", name: "stelar7", spell1Id: "4", spell2Id: "7", lockedIn: false },
          { uuid: 1, team: 1, skin: "043000", name: "FNC Jesiz", spell1Id: "3", spell2Id: "4", lockedIn: true },
          { uuid: 2, team: 1, skin: "101000", name: "FNC Caps", spell1Id: "21", spell2Id: "4", lockedIn: true },
          { uuid: 3, team: 1, skin: "079000", name: "FNC Broxah", spell1Id: "4", spell2Id: "11", lockedIn: true },
          { uuid: 4, team: 1, skin: "031000", name: "FNC sOAZ", spell1Id: "12", spell2Id: "4", lockedIn: true }
        ],
        teamB: [
          { uuid: 5, team: 2, skin: "150000", name: "TSM Hauntzer", spell1Id: "4", spell2Id: "7", lockedIn: true },
          { uuid: 6, team: 2, skin: "113000", name: "TSM Svenskeren", spell1Id: "3", spell2Id: "4", lockedIn: true },
          { uuid: 7, team: 2, skin: "134000", name: "TSM Bjergsen", spell1Id: "21", spell2Id: "4", lockedIn: true },
          { uuid: 7, team: 2, skin: "018000", name: "TSM Doublelift", spell1Id: "4", spell2Id: "11", lockedIn: true },
          { uuid: 9, team: 2, skin: "875000", name: "TSM Biofrost", spell1Id: "12", spell2Id: "4", lockedIn: true }
        ]
      }
    };
  },
  mounted() {
    const ref = this;
/*
    ref.bans = {
      teamA: [],
      teamB: [],
      center: {
        logo: ref.bans.center.logo
      }
    };

    ref.picks = {
      teamA: [],
      teamB: []
    };
*/
    const ws = new WebSocket("ws://localhost:2998");
    ws.onmessage = function(message: any) {
      const data = JSON.parse(message.data);
      switch (Object.keys(data)[0]) {
        //case "CHAMP_SELECT_STOP":
        case "RESET": {
          ref.bans = {
            teamA: [],
            teamB: [],
            center: {
              logo: ref.bans.center.logo
            }
          };

          ref.picks = {
            teamA: [],
            teamB: []
          };

          break;
        }
        case "CHAMP_SELECT_START": {
          const playerList = data["CHAMP_SELECT_START"];
          console.log(playerList);
          ref.picks.teamA = playerList.filter((s: any) => s.team == 1);
          ref.picks.teamB = playerList.filter((s: any) => s.team == 2);
          break;
        }
        case "BAN": {
          const obj = data["BAN"];
          //{"BAN":{"uuid":0,"champion":268,"lockedIn":false}}

          if (obj.lockedIn) {
            const onTeamA = ref.picks.teamA.filter(o => o.uuid == obj.uuid)[0];
            if (onTeamA) {
              ref.bans.teamA.push(obj.champion);
            } else {
              ref.bans.teamB.push(obj.champion);
            }
          }

          break;
        }
        case "SELECT": {
          // {"SELECT":{"uuid":0,"team":1,"name":"stelar7","spell1Id":"4","spell2Id":"7","skin":201002,"lockedIn":true}}
          const obj = data["SELECT"];
          console.log(obj);

          if (obj.team == 1) {
            ref.picks.teamA = ref.picks.teamA.map(p => (p.uuid == obj.uuid ? obj : p));
          } else {
            ref.picks.teamB = ref.picks.teamB.map(p => (p.uuid == obj.uuid ? obj : p));
          }

          break;
        }
        default: {
          //console.log(data);
        }
      }
    };
  }
});
</script>

<style scoped lang="scss">
#container {
  min-width: 1600px;
  height: 100%;
  width: 100%;
  display: flex;
  flex-direction: column;
}
#header {
  display: flex;
  width: 100%;
  height: 20vh;
}

#center {
  display: flex;
  flex: 1 0;
  align-items: stretch;
  width: 100%;
  height: 100%;
}

#footer {
  display: flex;
  width: 100%;
  height: 20vh;
}
</style>
