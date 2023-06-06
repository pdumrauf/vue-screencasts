<template>
  <div class="home">
    <h1>Videos</h1>
    <div class="video-container">
      <div v-for="video in videos" :key="video.name" class="video-box">
        <router-link :to="{ name: 'video-watch', params: { id: video.id } }">
          <img :src="video.thumbnail" alt="video-thumbnail">
          <div>
            <h3>{{ video.name }}</h3>
            <div v-html="video.description"></div>
          </div>
        </router-link>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: 'HomeView',
  components: {
  },
  data() {
    return {
      videos: this.$store.state.videos
    }
  }
}
</script>

<style scoped lang="scss">
  .video-container {
    .video-box {
      display: flex;
      border: 1px solid black;
      border-radius: 10px;
      margin: 10px;
      padding: 10px;
      text-align: left;

      img {
        width: 200px;
        padding: 10px;
      }
    }
  }
</style>
