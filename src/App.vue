<template>
  <v-app>
    <v-app-bar
      flat
      app
    >
      <!--Logo-->
      <v-app-bar-title
        class="text-uppercase"
      >
        Logogo
      </v-app-bar-title>

      <!--Menu-->
      <v-menu offset-y>
        <template v-slot:activator="{ on, attrs }">
          <v-btn
            color="grey"
            text
            v-bind="attrs"
            v-on="on"
          >
            <v-icon left> mdi-chevron-down</v-icon>
            <span>Menu</span>
          </v-btn>
        </template>
        <v-list>
          <v-list-item
            v-for="(item, index) in items"
            :key="index"
            router :to="item.route"
          >
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item>
        </v-list>
      </v-menu>

      <!--Avatar-->
      <v-layout column align-end>
        <v-flex>
          <v-avatar class="mr-3" color="black">
            <img src="/avatar.jpeg" alt="avatar">
          </v-avatar>
          <span>Котофей Иванович</span>
        </v-flex>
      </v-layout>
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
  data() {
    return {
      items: [
        {
          title: 'Films',
          icon: 'mdi-movie',
          route: '/',
        },
        {
          title: 'Serials',
          icon: 'mdi-video',
          route: '/films',
        },
        {
          title: 'TV-shows',
          icon: 'mdi-television-box',
          route: '/',
        },
        {
          title: 'Films',
          icon: 'mdi-movie',
          route: '/films',
        },
        {
          title: 'Serials',
          icon: 'mdi-video',
          route: '/films',
        },
        {
          title: 'TV-shows',
          icon: 'mdi-television-box',
          route: '/films',
        },
      ],
    };
  },
};
</script>
