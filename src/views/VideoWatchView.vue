<template>
  <div>
    <img :src="video.thumbnail" alt="video-thumbnail">
    <h1>{{ video.name }}</h1>
    <div v-html="video.description"></div>
  </div>
</template>

<script>
  export default {
    name: 'VideoWatchView',
    computed: {
      video() {
        return this.$store.state.videos.find(video => video.id == this.$route.params.id)
      }
    }
  }
</script>

<style lang="scss" scoped>
  img {
    max-width: 50%;
  }
</style>