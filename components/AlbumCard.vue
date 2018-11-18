<template lang="html">
  <div class="column is-one-quarter">
    <div class="box">
      <h3>{{album.title}}</h3>
      <nuxt-link class="button is-primary" :to="`/albums/${album.id}`">Ver álbum</nuxt-link>
    </div>
  </div>
</template>

<script>
export default {
  name: 'AlbumCard',
  props:{
    album: Object
  }
}
</script>

<style lang="css">
.box{
  padding: 1em;
}
h3{
  min-height: 5em;
}
</style>
