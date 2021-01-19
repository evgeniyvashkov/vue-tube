<template>
  <li class="list-group-item media" @click="onVideoSelect">
    <img class="me-3" :src="thumbnailsUrl"/>
    <div class="media-body">
      {{ video.snippet.title }}
    </div>
  </li>
</template>

<script>
export default {
  name: 'VideoListItem',
  props: ['video'],
  computed: {
    thumbnailsUrl() {
      return this.video.snippet.thumbnails.default.url;
    }
  },
  methods: {
    onVideoSelect() {
      this.$emit('onVideoSelect', this.video)
    }
  }
}
</script>

<style scoped>
li {
  width: 100%;
  display: flex;
  align-items: flex-start;
  cursor: pointer;
}

li:hover {
  background: #eee;
}
</style>