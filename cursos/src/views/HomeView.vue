<template>
  <v-container>
    <v-row>
      <v-col v-for="curso in cursos" :key="curso.id">
        <v-card width="400">
          <v-img
            height="200px"
            :src="curso.img"
          >
            <v-app-bar flat color="rgba(0, 0, 0, 0)">         
            
            </v-app-bar>
          </v-img>
          <v-card-title>{{curso.nombre}}</v-card-title>
          <v-card-text>
            <div class="font-weight-bold ml-8 mb-2">Información</div>

            <v-timeline align-top dense>
              <v-timeline-item
                color="deep-purple lighten-1"
                small
              >
                <div>
                  <div class="font-weight-normal">
                    costo: <strong>{{ curso.costo }} </strong>
                  </div>
                  <div>duración: {{ curso.duracion }}</div>
                </div>
              </v-timeline-item>

              <v-timeline-item
                color="green"
                small
              >
                <div>
                  <div class="font-weight-normal">
                    cupos: <strong>{{ curso.cupos }} </strong>
                  </div>
                  <div>completado: {{ (curso.completado?'Sí':'No') }}</div>
                </div>
              </v-timeline-item>

              <v-timeline-item
                color="deep-purple lighten-1"
                small
              >
                <div>
                  <div class="font-weight-normal">
                    Fecha de Registro:
                  </div>
                  <div>{{ curso.fecha_registro }}</div>
                </div>
              </v-timeline-item>

              <v-timeline-item
                color="green"
                small
              >
                <div>
                  <div class="font-weight-normal">
                    Descripción: 
                  </div>
                  <div>{{ curso.descripcion}}</div>
                </div>
              </v-timeline-item>
            </v-timeline>
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import { mapState } from "vuex";

export default {
  name: "HomeView",
  data: function () {
    return {
    };
  },
  components: {},
  computed: {
    ...mapState(["cursos"]),
  },
};
</script>
