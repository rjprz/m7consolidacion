<template>
  <v-container>
    <v-row class="d-flex justify-center my-6">
      <h1 >Administración</h1>
    </v-row>
    <v-row class="d-flex justify-center mb-3">
      <v-btn color="primary">AGREGAR CURSO</v-btn>
    </v-row>
    <TablaCursos/>
  </v-container>
</template>

<script>
import TablaCursos from '@/components/TablaCursos.vue';
export default {
  name: 'admin-comp',
  // props: {},
  data: function(){
    return {}
  },
  // computed: {},
  //methods: {},
  // watch: {},
  components: {
    TablaCursos
  },
  // mixins: [],
  // filters: {},
  // -- Lifecycle Methods
  // -- End Lifecycle Methods
}
</script>

<style scoped>
  h1{
    font-size: 60px;
    font-weight: 400;
  }
</style>