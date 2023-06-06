<template>
  <div>
    <h1>Hi, let's watch a video</h1>
    <h3>{{ this.$route.params.id }}</h3>
    {{ video.name }}
  </div>
</template>

<script>
  export default {
    name: 'VideoWatchView',
    computed: {
      video() {
        return this.$store.state.videos.find(video => video.name === this.$route.params.id)
      }
    }
  }
</script>

<style lang="scss" scoped>

</style>