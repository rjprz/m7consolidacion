<template>
  <v-app>
    <v-app-bar
      app
      color="primary"
      dark
    >
      <div class="d-flex align-center">
        <v-img
          alt="Vuetify Logo"
          class="shrink mr-2"
          contain
          src="https://cdn.vuetifyjs.com/images/logos/vuetify-logo-dark.png"
          transition="scale-transition"
          width="40"
        />

        <v-img
          alt="Vuetify Name"
          class="shrink mt-1 hidden-sm-and-down"
          contain
          min-width="100"
          src="https://cdn.vuetifyjs.com/images/logos/vuetify-name-dark.png"
          width="100"
        />
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
