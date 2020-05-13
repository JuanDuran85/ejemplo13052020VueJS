<template>
  <div class="container">
    <h1>Muestra de Series</h1>
    <series :informacion="series"></series>
    <modal v-for="(item, index) in series" :key="index" :imagen="item.image.medium" :descrip="item.summary" :nombre="item.name" :index="index"></modal>
  </div>
</template>

<script>
import axios from 'axios';
import Series from './components/Series.vue';
import Modal from './components/Modal.vue';

export default {
  name: 'App',
  data() {
    return {
      series: []
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
    Modal
  }
}
</script>

<style>

</style>
