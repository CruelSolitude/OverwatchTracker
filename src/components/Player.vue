<template>
  <div class="player-box">
    <div class="player-container" v-if="playerJson.ready">
      <h2>{{ player.name }}</h2>
      <img class="profile-picture" :src="playerJson.state.icon" alt="" />
      <img :src="playerJson.state.ratingIcon" alt="" />
      <h3>Current Rank:</h3>
      <h3>{{ playerJson.state.ratings[1].level }} SR</h3>
    </div>
    <pulse-loader
      v-else
      :loading="loading"
      color="#636363"
      :size="size"
    ></pulse-loader>
  </div>
</template>

<script>
import { useAsyncState } from "@vueuse/core";
import PulseLoader from "vue-spinner/src/PulseLoader.vue";

export default {
  created() {
    this.getData(this.player.battletag);
  },
  data() {
    return {
      playerJson: useAsyncState(this.getData(this.player.battletag)),
    };
  },
  components: {
    PulseLoader,
  },
  methods: {
    async getData(battletag) {
      const response = await fetch(
        `https://ow-api.com/v1/stats/pc/eu/${battletag}/profile`
      );
      return response.json();
    },
  },
  props: {
    player: Object,
  },
};
</script>

<style scoped>
.player-box {
  border-radius: 50px;
  background: #ffffff;
  box-shadow: 29px 29px 58px #d9d9d9, -29px -29px 58px #ffffff;
  padding: 20px;
  min-height: 300px;
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 20px;
}
.player-box * {
  margin: 20px 0px;
}
.player-box img {
  max-width: 150px;
  width: 70%;
}
.player-container {
  display: flex;
  flex-direction: column;
  align-items:center;
}
.profile-picture {
  clip-path: circle(50%);
}
</style>