<template>
  <div class="col-md-4">
    <ul class="list-group">
      <video-list-item 
        v-for="video in videos" 
        :video="video"
        :key="video.etag"
        @videoSelect="onVideoSelect"
      />
    </ul>
  </div>
</template>

<script>
  import VideoListItem from './VideoListItem';

  export default {
    name: 'VideoList',
    components: {
      videoListItem: VideoListItem
    },
    props: {
      videos: Array
    },
    methods: {
      onVideoSelect(video){
        this.$emit('videoSelect', video);
      }
    }
  }
</script>

<style>
  
</style>