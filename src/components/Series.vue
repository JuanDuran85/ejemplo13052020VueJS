<template>
  <div>
    <h2>Series TV</h2>
    <div class="row">
      <div v-for="(serie, index) in informacion" :key="index" class="col-12 col-sm-12 col-md-6 col-lg-3 col-xl-3 d-flex align-items-stretch">
        <div class="card my-2">
          <img :src="serie.image.medium" class="card-img-top" alt="">
          <div class="card-body">
            <h5 class="card-title">{{serie.name | mayusculas }}</h5>
            <p class="card-text text-justify" v-html="$options.filters.recorte(serie.summary)"></p>
            <button type="button" class="btn btn-primary boton1" :class="{ boton2: activo }" data-toggle="modal" :data-target="'#ventana'+index">
            Var más
            </button>
          </div>
        </div>
        <modal :key="index" :id="'id'+index" :imagen="serie.image.medium" :descrip="serie.summary" :nombre="serie.name"></modal>
      </div>
    </div>
    
  </div>
</template>

<script>
import Modal from './Modal.vue';

export default {
  name: 'Series',
  data() {
    return {
      activo: false
    }
  },
  props: { 
    informacion: {
      type: Array,
      required: true,
      datatarget: 'data-target'
    } 
  },
  components: {
    Modal
  },
  filters: {
    mayusculas(texto){
      return texto.toUpperCase();
    },
    recorte(texto){
      return texto.substring(0,100)+'...';
    }
  },

  methods: {
    eventos () {
      console.log(this)
    }
  }
}
</script>

<style scoped>
.boton1:hover{
  background-color: crimson;
}
.boton2 {
  background-color: chartreuse;
  font-size: 24px;
}
</style>
