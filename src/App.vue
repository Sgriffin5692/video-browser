<template>
    <div>
        <SearchBar @termChange="onTermChange"></SearchBar>
    </div>
</template>

<script>
  import SearchBar from './components/SearchBar';
  import axios from 'axios';
  const API_KEY = '';

  export default {
    name: 'App',
    components: {SearchBar},
    methods: {
      onTermChange: function(searchTerm) {
        axios.get('https://www.googleapis.com/youtube/v3/search', {
          params: {
            key: API_KEY,
            type: 'video',
            part: 'snippet',
            q: searchTerm
          }
        }).then(response => console.log(response))
      }
    }
  };
</script>