<template>
  <div class="container">
    <h1>Muestra de Series</h1>
    <series></series>
  </div>
</template>

<script>
import axios from 'axios';
import Series from './components/Series.vue';

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
    Series
  }
}
</script>

<style>

</style>
