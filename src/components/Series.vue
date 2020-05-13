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
            <button type="button" class="btn btn-primary" data-toggle="modal" :data-target="'#ventana'+index">
            Var más
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Series',
  props: { 
    informacion: {
      type: Array,
      required: true,
    } 
  },
  filters: {
    mayusculas(texto){
      return texto.toUpperCase();
    },
    recorte(texto){
      return texto.substring(0,100)+'...';
    }
  }
}
</script>

<style scoped>

</style>
