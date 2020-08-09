<template>
    <div class="container">
        <SearchBar @termChange="onTermChange"></SearchBar>
        <VideoList :videos="videos"></VideoList>
    </div>
</template>

<script>
  import SearchBar from './components/SearchBar';
  import VideoList from './components/VideoList'
  import axios from 'axios';
  const API_KEY = '';

  export default {
    name: 'App',
    components: {VideoList, SearchBar},
    data() {
      return { videos: []};
    },
    methods: {
      onTermChange: function(searchTerm) {
        axios.get('https://www.googleapis.com/youtube/v3/search', {
          params: {
            key: API_KEY,
            type: 'video',
            part: 'snippet',
            q: searchTerm
          }
        }).then(response => {
          this.videos = response.data.items;
        })
      }
    }
  };
</script>