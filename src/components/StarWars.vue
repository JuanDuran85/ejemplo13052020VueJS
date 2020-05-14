<template>
  <div>
      <h3>Star Wars</h3>
      <ul>
          <li v-for="(item, index) in personajes" :key="index">{{item.name}}</li>
      </ul>
  </div>
</template>

<script>
import axios from 'axios';

export default {
    name: 'StarWar',
    data() {
        return {
            personajes: []
        }
    },
    methods: {
       async personStar(){
            try {
                const respuesta = await axios.get('https://swapi.dev/api/people/');
                console.log(respuesta.data.results);
                this.personajes = respuesta.data.results;
            } catch (error) {
                console.error(error);
            }
        }
    },
    mounted() {
        this.personStar();
    }
}
</script>

<style>

</style>