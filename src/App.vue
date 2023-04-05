<template>
  <v-app>
    <v-app-bar
      flat
      app
    >
      <v-app-bar-title
        class="text-uppercase"
      >
        Logogo
      </v-app-bar-title>
    </v-app-bar>
    <NavBar/>
    <v-content class="grey lighten-4">
      <router-view/>
    </v-content>
  </v-app>
</template>

<script>
import NavBar from '@/components/NavBar.vue';

export default {
  name: 'App',
  components: { NavBar },
};
</script>
