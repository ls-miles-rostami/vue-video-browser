<template>
  <li class='list-group-item media' @click="onVideoSelect">
    <img class='mr-3' :src="thumbnailUrl" />
   <div class="media-body">
     <h5 class="mt-0 mb-1">{{video.snippet.title}}</h5>
     
   </div>
  </li>
</template>
<script>
export default {
  name: 'VideoListItem',
  props: ['video'],
  methods: {
    onVideoSelect() {
      this.$emit('videoSelect', this.video);
    }
  },
  computed: {
    thumbnailUrl() {
      return this.video.snippet.thumbnails.default.url;
    }
  }
};
</script>
<style scoped>
li {
  display: flex;
}
li:hover {
  background-color: #eee;
  cursor: pointer;
}
</style>
