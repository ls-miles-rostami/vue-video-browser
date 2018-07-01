<template>
  <ul class='list-group col-md-4'>
    <app-video-list-item v-for='video in videos' :video='video' :key="video.etag" @videoSelect='onVideoSelect'></app-video-list-item>
  </ul>
</template>
<script>
import VideoListItem from './VideoListItem.vue';
export default {
  name: 'VideoList',
  props: ['videos'],
  methods: {
    onVideoSelect(video) {
      this.$emit('videoSelect', video)
    }
  },
  components: {
    appVideoListItem: VideoListItem
  }
};
</script>
<style>
</style>
