<template>
  <v-app>
    <v-app-bar
      app
      color="primary"
      dark
    >
      <div class="d-flex align-center">
      <span>Cursos AlfaWeb</span>
      </div>

      <v-spacer></v-spacer>

      <v-btn
        text
        @click="redirectTo('home')"
      >
        <v-icon>mdi-home</v-icon>
      </v-btn>
      <v-btn
        text
        @click="redirectTo('administracion')"
      >
        <v-icon>mdi-tools</v-icon>
      </v-btn>
    </v-app-bar>

    <v-main>
      <router-view/>
    </v-main>
  </v-app>
</template>

<script>

export default {
  name: 'App',

  data: () => ({
    //
  }),
  computed: {
    currentRouteName(){
      return this.$route.name;
    }
  },
  methods: {
    redirectTo(nameRoute){
      if(this.currentRouteName == nameRoute) return;
      this.$router.push({name:nameRoute})
    },
  },
};
</script>
