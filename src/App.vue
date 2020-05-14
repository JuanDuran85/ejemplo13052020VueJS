<template>
  <div class="container">
    <h1>Muestra de Series</h1>
    <button class="btn btn-primary mx-2" @click="seleccion='Series'">Ver Series</button>
    <button class="btn btn-primary mx-2" @click="seleccion='Post'">Ver Post</button>
    <button class="btn btn-primary mx-2" @click="seleccion='StarWars'">Ver Star Wars</button>
    <keep-alive>
      <component :is="seleccion" :informacion="series"></component>
    </keep-alive>

    <!-- <series :informacion="series"></series>
    <post></post>
    <star-wars></star-wars> -->
    
    <modal v-for="(item, index) in series" :key="index" :imagen="item.image.medium" :descrip="item.summary" :nombre="item.name" :index="index"></modal>
  </div>
</template>

<script>
import axios from 'axios';
import Series from './components/Series.vue';
import Modal from './components/Modal.vue';
import Post from './components/Post.vue';
import StarWars from './components/StarWars.vue';

export default {
  name: 'App',
  data() {
    return {
      series: [],
      seleccion: 'Post'
    }
  },
  mounted() {
    axios.get('http://api.tvmaze.com/shows')
    .then(response => {
      console.log(response.data);
      this.series = response.data;
    })
    .catch(error => console.log(error))
  },
  components: {
    Series,
    Modal,
    Post,
    StarWars
  },
  beforeDestroy() {
      console.log("destruido");
  },
  destroyed() {
    console.log("destruido");
  },
}
</script>

<style>

</style>
