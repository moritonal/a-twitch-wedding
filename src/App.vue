<template>
  <div id="app">
    <div class="container-fluid overflow-hidden">
      <div class="row">
        <div class="d-flex col-lg-12 justify-content-center pt-5 pb-2">
          <h2>Tish and Tom</h2>
        </div>
      </div>
      <div class="row">
        <div class="d-flex col-lg-12 justify-content-center p-2">
          <TwitchPlayer/>
        </div>
      </div>
      <div class="row">
        <div class="d-flex col-lg-12 justify-content-center p-2">
          <h2>San Francisco, City Hall</h2>
        </div>
      </div>
      <div class="row">
        <div class="d-flex col-lg-12 justify-content-center p-2 text-center">
          <h3>{{localTime}}<br>in {{diff}}</h3>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import TwitchPlayer from "./components/TwitchPlayer";
import GoogleMap from "./components/GoogleMap";
import Chat from "./components/Chat";
import moment from "moment";

@Component({
  components: {
    TwitchPlayer,
    GoogleMap,
    Chat
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
    return this.targetUtc.local().format("Do MMMM YYYY [at] HH:mm [your time]");
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
