<template>
  <div class="title">
    <h1>Overwatch Friends &#128522;</h1>
  </div>
  <div class="container">
    <div class="row row-cols-1 row-cols-md-2 row-cols-lg-3">
      <div class="col" v-for="player in players" :key="player.name">
        <Player :player="player" />
      </div>
    </div>
  </div>
</template>

<script>
import Player from "./components/Player.vue";

export default {
  data() {
    return {
      players: [
        {
          name: "Elias",
          battletag: "SampleText-21568",
        },
        {
          name: "Jan",
          battletag: "kyoza-2904",
        },
        {
          name: "Michael",
          battletag: "Eto-21118",
        },
      ],
    };
  },
  components: {
    Player,
  },
  methods: {},
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  min-height: 100vh;
  width: 100vw;
}
.title {
  height: 200px;
  display: flex;
  justify-content: center;
  align-items: center;
  margin-bottom: 30px;
}
.title h1 {
  border-radius: 50px;
  background: #ffffff;
  border-radius: 50px;
  background: #ffffff;
  box-shadow: 15px 15px 30px #d9d9d9, -15px -15px 30px #ffffff;
  padding: 30px;
  margin: 0px;
}
</style>
