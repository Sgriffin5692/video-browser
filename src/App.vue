<template>
    <div class="container">
        <div class ="row justify-content-center m-2">
            <SearchBar @termChange="onTermChange"></SearchBar>
            <div class="my-auto">
                <button @click="onClick" class="btn btn-primary">Search</button>
            </div>
        </div>
        <div class="row">
            <VideoDetail :video="selectedVideo"></VideoDetail>
            <VideoList @videoSelect="onVideoSelect" :videos="videos"></VideoList>
        </div>
    </div>
</template>

<script>
  import SearchBar from './components/SearchBar';
  import VideoList from './components/VideoList'
  import VideoDetail from './components/VideoDetail';
  import axios from 'axios';
  const API_KEY = '';

  export default {
    name: 'App',
    components: {VideoList, SearchBar, VideoDetail},
    data() {
      return { videos: [], selectedVideo: null, searchTerm: null};
    },
    methods: {
      onTermChange: function(searchTerm) {
        this.searchTerm = searchTerm;
      },
      onVideoSelect(selectedVideo) {
        this.selectedVideo = selectedVideo;
      },
      onClick() {
        if(this.searchTerm != null) {
          axios.get('https://www.googleapis.com/youtube/v3/search', {
            params: {
              key: API_KEY,
              type: 'video',
              part: 'snippet',
              q: this.searchTerm
            }
          }).then(response => {
            this.videos = response.data.items;
          })
        }
      }
    }
  };
</script>