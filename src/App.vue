<template>
    <div class="container">
        <search-bar @termChange="onTermChange" />
        <div class="row">
          <video-detail :video="selectedVideo"></video-detail>
          <video-list :videos="videos" @videoSelect="onVideoSelect" />
        </div>
    </div>
</template>

<script>
  import axios from 'axios';
  import SearchBar from './components/SearchBar';
  import VideoList from './components/VideoList';
  import VideoDetail from './components/VideoDetail';
  const API_KEY = 'AIzaSyBboWgZIwJhWXGt4gUuoEwgHfxirpExn5g';

  export default {
    name: 'App',
    data() {
      return {
        searchingTimer: null,
        videos: [],
        selectedVideo: null
      };
    },
    methods: {
      onTermChange(searchTerm){
        if(this.searchingTimer){
          clearTimeout(this.searchingTimer);
        }
        this.searchingTimer = window.setTimeout( ()=> {
          axios.get('https://www.googleapis.com/youtube/v3/search', { 
            params: {
              key: API_KEY,
              type: 'video',
              part: 'snippet',
              q: searchTerm
            }
          })
            .then( response => {
              this.searchingTimer = null;
              this.videos = response.data.items 
            });
        }, 1000 );
      },
      onVideoSelect(video){
        this.selectedVideo = video;
      }
    },
    components: {
      searchBar: SearchBar,
      videoList: VideoList,
      videoDetail: VideoDetail
    }
  }
</script>

<style>
    
</style>