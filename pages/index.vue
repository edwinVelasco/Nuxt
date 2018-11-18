<template lang="html">
  <div class="container">
    <header>
      <h1 class="title">{{status}}, Albums de la pagina</h1>
      <button type="button" name="button" v-on:click="reverseStatus">
        Reverse Status
      </button>
    </header>
    <div class="columns is-multiline">
      <AlbumCard :album="album" v-for="album in albums" :key="album.id"/>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import env from '../config/env';
import AlbumCard from '../components/AlbumCard';
export default {
  name: "IndexPage",
  components:{
    AlbumCard
  },
  data(){
    return {
      status: 'hola',
      albums: []
    }
  },
  methods: {
    reverseStatus: function(){
      this.status = String(this.status).split("").reverse().join('')
    }
  },
  created: async function(){
    let dataResponse = await axios.get(`${env.endpoint}/albums`);
    this.status = dataResponse.status;
    this.albums = dataResponse.data;
  }
}
</script>

<style scoped>
</style>
