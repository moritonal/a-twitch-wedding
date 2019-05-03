<template>
  <div>
    <iframe 
      width="560" 
      height="315" 
      src="https://www.youtube.com/embed/v8ZwdHbdofg?autoplay=1" 
      frameborder="0"
      allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture"
      allowfullscreen>
    </iframe>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";

@Component({
  components: {}
})
export default class YoutubePlayer extends Vue {
  mounted() {

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

#twitch-embed {
  width: 70vmin;
  height: calc(63vmin / (16/9));
}

</style>
