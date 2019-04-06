<template>
  <div class="major">
    <div id="twitch-embed"></div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";

module Twitch {}

@Component({
  components: {}
})
export default class TwitchPlayer extends Vue {
  mounted() {

    var embed = new Twitch.Embed("twitch-embed", {
      width: "100%",
      height: 480,
      layout: "video",
      theme: "dark",
      channel: "moritonal"
    });

    embed.addEventListener(Twitch.Embed.VIDEO_READY, () => {
      console.log("Player is reading");
    });

    embed.addEventListener(Twitch.Embed.VIDEO_PLAY, id => {
      console.log("Player is playing", id);
    });
  }
}
</script>

<style>

.major {
  width: 90%;
}

</style>
