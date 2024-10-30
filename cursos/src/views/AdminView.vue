<template>
  <v-container>
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
  
</style>