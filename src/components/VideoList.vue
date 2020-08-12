<template>
    <div class="col-md-4 mx-auto">
        <ul class="list-group">
            <VideoListItem v-for="video in videos"
                           :key="video.etag"
                           :video="video"
                           @videoSelect="onVideoSelect"></VideoListItem>
        </ul>
    </div>
</template>

<script>
  import VideoListItem from './VideoListItem';

  export default {
      name: 'VideoList',
      components: {VideoListItem},
      props: ['videos'],
      methods: {
        onVideoSelect(video) {
          this.$emit("videoSelect", video)
        }
      }
    };
</script>

<style scoped>
    div {
        display: flex;
    }
</style>