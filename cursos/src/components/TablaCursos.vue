<template>
  <v-container class="fill-height">
    <v-row class="d-flex justify-center">
      <v-col xl="8">
        <v-simple-table>
          <template v-slot:default>
            <thead>
              <tr>
                <th class="text-left">Curso</th>
                <th class="text-left">Cupos</th>
                <th class="text-left">Inscritos</th>
                <th class="text-left">Duración</th>
                <th class="text-left">Costo</th>
                <th class="text-left">Terminado</th>
                <th class="text-left">Fecha</th>
                <th class="text-left">Acciones</th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="curso in cursos" :key="curso.id">
                <td>{{ curso.nombre }}</td>
                <td>{{ curso.cupos }}</td>
                <td>{{ curso.inscritos }}</td>
                <td>{{ curso.duracion }}</td>
                <td>
                  <v-chip color="green lighten-1"> {{ curso.costo }} </v-chip>
                </td>
                <td>
                  <v-chip color="grey">
                    {{ curso.completado ? "Sí" : "No" }}
                  </v-chip>
                </td>
                <td>
                  <v-chip color="green lighten-1">{{
                    curso.fecha_registro
                  }}</v-chip>
                </td>
                <td>
                  <v-btn text>
                    <v-icon color="amber ">mdi-pencil</v-icon>
                  </v-btn>
                  <v-btn text>
                    <v-icon @click="borrar(curso.id)" color="red darken-2">mdi-delete</v-icon>
                  </v-btn>
                </td>
              </tr>
            </tbody>
          </template>
        </v-simple-table>
      </v-col>
    </v-row>
    <v-divider class="ma-6" inset></v-divider>
    <v-row>
      <v-col>
        <v-row class="d-flex justify-center mb-3">
          <v-chip color="purple" label outlined large>
            <v-icon>mdi-account-multiple</v-icon>
            Cantidad total de alumnos permitidos: {{ totalAlumnos }} alumnos
          </v-chip>
        </v-row>
        <v-row class="d-flex justify-center mb-3">
          <v-chip color="light-blue" label outlined large>
            <v-icon>mdi-account-multiple-check</v-icon>
            Cantidad total de alumnos inscritos: {{ totalInscritos }} alumnos
          </v-chip>
        </v-row>
        <v-row class="d-flex justify-center mb-3">
          <v-chip color="red" label outlined large>
            <v-icon>mdi-account-multiple-plus</v-icon>
            Cantidad total de cupos restantes: {{ cuposRestantes }} cupos
          </v-chip>
        </v-row>
        <v-row class="d-flex justify-center mb-3">
          <v-chip color="pink" label outlined large>
            <v-icon>mdi-cancel</v-icon>
            Cantidad total de cursos terminados: {{ cursosTerminados }} cursos
          </v-chip>
        </v-row>
        <v-row class="d-flex justify-center mb-3">
          <v-chip color="lime darken-3" label outlined large>
            <v-icon>mdi-bell-ring</v-icon>
            Cantidad total de cursos activos: {{ cursosActivos }} cursos
          </v-chip>
        </v-row>
        <v-row class="d-flex justify-center mb-3">
          <v-chip color="orange" label outlined large>
            <v-icon>mdi-bell-ring</v-icon>
            Cantidad total de cursos: {{ totalCursos }} cursos
          </v-chip>
        </v-row>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import { mapState, mapActions, mapGetters } from "vuex";
export default {
  name: "tabla-comp",
  // props: {},
  data: function () {
    return {};
  },
  computed: {
    ...mapState(["cursos"]),
    ...mapGetters(['getCursos']),
    totalAlumnos() {
      return this.cursos.reduce(
        (accumulator, currentValue) => accumulator + currentValue.cupos,
        0
      );
    },
    totalInscritos() {
      return this.cursos.reduce(
        (accumulator, currentValue) => accumulator + currentValue.inscritos,
        0
      );
    },
    cuposRestantes() {
      return this.totalAlumnos - this.totalInscritos;
    },
    cursosTerminados() {
      return this.cursos.filter((curso) => curso.completado).length;
    },
    cursosActivos() {
      return this.cursos.length - this.cursosTerminados;
    },
    totalCursos() {
      return this.cursos.length;
    },
  },
  methods: {
    ...mapActions(['borrarCurso']),
    borrar(id){
      let index =  this.getCursos.findIndex((curso) => curso.id === id)
      this.borrarCurso(index)

    }
   
  },
  // watch: {},
  // components: {},
  // mixins: [],
  // filters: {},
  // -- Lifecycle Methods
  // mounted(){
  //   console.log(this.totalAlumnos);
  // }
  // -- End Lifecycle Methods
};
</script>

<style scoped></style>
