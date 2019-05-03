<template>
  <div id="app">
    <div class="container-fluid overflow-hidden">
      <div class="row px-4">
        <div class="d-flex col-md-12 justify-content-center p-0 flex-column pt-4">
        <div class="text-center p-3">
        <h2>Tish and Tom</h2>
          <h2>San Francisco, City Hall</h2>
          <h3>{{localTime}}</h3>
        </div>
        </div>
      </div>
      <div class="row px-4">
        <div class="d-flex col-lg-7 justify-content-center p-2">
        </div>
        <div class="d-flex col-lg-5 align-items-center flex-column pt-0">
          <YoutubePlayer></YoutubePlayer>
        </div>
      </div>
      <div class="row pt-4">
        <div class="d-flex col-lg-12 justify-content-center p-2">
        </div>
      </div>
      <div class="row">
        <div class="d-flex col-lg-5 justify-content-center p-2 text-center">
        </div>
        <div class="d-flex col-lg-7 justify-content-center p-2">
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import TwitchPlayer from "./components/TwitchPlayer";
import YoutubePlayer from "./components/YoutubePlayer";
import moment from "moment";

@Component({
  components: {
    TwitchPlayer,
    YoutubePlayer
  },
  data: () => {
    return {
      now: moment(),
      interval: null,
      targetUtc: null
    };
  }
})
export default class App extends Vue {
  now: any;
  interval: any;
  targetUtc: moment.Moment = moment();

  constructor() {
    super();
  }

  created() {

    this.targetUtc = moment.utc("2019-04-15T20:30");

    this.interval = setInterval(() => {
      this.now = moment();
    }, 1000);
  }

  get localTime() {
    return this.targetUtc.local().format("HH:mm[ - ]DD[ | ]MM[ | ]YYYY");
  }

  get diff() {
    let localTarget = this.targetUtc.local();
    let localTime = this.now;

    let diff = moment.duration(localTarget.diff(localTime));

    return `${diff.days()} days, ${diff.hours()} hours, ${diff.minutes()} minutes and ${diff.seconds()} seconds`;
  }

  destroyed() {
    clearInterval(this.interval);
  }
}
</script>

<style>
#app {
  font-family: "ASongForJennifer", serif;

  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
