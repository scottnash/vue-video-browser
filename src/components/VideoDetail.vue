<template>
  <div v-if="video" class="col-md-8">
    <div class="embed-responsive embed-responsive-16by9">
      <iframe
        class="embed-responsive-item"
        :src="videoUrl" 
        frameborder="0" 
      ></iframe>
    </div>
    <div class="details">
      <h4>{{ video.snippet.title }}</h4>
      <p>{{ video.snippet.description }}</p>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'VideoDetail',
    props: ['video'],
    computed: {
      videoUrl() {
        return `https://www.youtube.com/embed/${ this.video.id.videoId }`;
      }
    }
  }
</script>

<style scoped>
  .details {
    border: 1px solid #ddd;
    border-radius: 4px;
    margin: 10px 0;
    padding: 10px;
  }

</style>