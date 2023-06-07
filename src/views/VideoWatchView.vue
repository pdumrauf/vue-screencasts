<template>
  <div>
    <video-player class="video-player-box"
                  ref="videoPlayer"
                  :options="playerOptions">
    </video-player>
    <h1>{{ video.name }}</h1>
    <div v-html="video.description"></div>
  </div>
</template>

<script>
import 'video.js/dist/video-js.css'
import { videoPlayer } from 'vue-video-player'

  export default {
    name: 'VideoWatchView',
    components: {
      videoPlayer
    },
    computed: {
      video() {
        return this.$store.state.videos.find(video => video.id == this.$route.params.id)
      },
      playerOptions() {
        return {
          language: 'en',
          playbackRates: [0.7, 1.0, 1.5, 2.0, 2.5, 3.0],
          sources: [{
            type: "video/mp4",
            src: this.video.videoUrl
          }],
          poster: this.video.thumbnail,
        }
      }
    }
  }
</script>

<style lang="scss">
  .video-player-box {
    .video-js {
      width: 80%;
      margin: auto;
      height: 700px;
    }
    .vjs-poster {
      background-size: cover;
      width: 100%;
    }
  }
</style>