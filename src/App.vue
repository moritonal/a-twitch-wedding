<template>
  <div id="app">
        <div class="container-fluid m-0 p-0 overflow-hidden">
            <div class="row">
                <div class="d-flex col-lg-12 justify-content-center p-5">
                    <h2>Tish and Tom - 15th April 2019</h1>
                </div>
            </div>
            <div class="row">
                <div class="d-flex col-lg-12 justify-content-center">
                    <TwitchPlayer/>
                </div>
            </div>
            <div class="row">
                <div class="d-flex col-lg-12 justify-content-center p-5">
                    <h2>San Francisco, City Hall</h2>
                </div>
            </div>
        </div>
  </div>
</template>

<script lang="ts">

import { Component, Vue } from 'vue-property-decorator';
import TwitchPlayer from "./components/TwitchPlayer";
import GoogleMap from "./components/GoogleMap";
import Chat from "./components/Chat";

@Component({
  components: {
    TwitchPlayer,
    GoogleMap,
    Chat
  },
})
export default class App extends Vue {

}

</script>

<style>

#app {
  font-family: 'Playfair Display SC', serif;

  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

</style>
