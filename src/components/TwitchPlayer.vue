<template>
  <div>
    <div id="twitch-embed" class="justify-content-flex-end"></div>
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
      height: "100%",
      width: "100%",
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

iframe {
  max-width: 90%;
}

#twitch-embed {
  justify-content: center;
  display: flex;
}

.justify-content-flex-end {
}

#twitch-embed {
  width: 70vmin;
  height: calc(63vmin / (16/9));
}

</style>
