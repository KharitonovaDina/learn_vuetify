<template>
  <v-navigation-drawer
    tag="nav"
    color="#1E1717"
    dark
    width="235px"
  >
    <h3 class="text-h4 white--text px-2 text-uppercase">
      Filmoteka
    </h3>
    <v-list
      nav
    >
      <v-list-item
        v-for="item in items"
        :key="item.title"
      >
        <v-list-item-icon>
          <v-icon>{{ item.icon }}</v-icon>
        </v-list-item-icon>

        <v-list-item-content>
          <v-list-item-title>{{ item.title }}</v-list-item-title>
        </v-list-item-content>
      </v-list-item>
    </v-list>
  </v-navigation-drawer>
</template>

<script>
export default {
  name: 'NavBar',

  data() {
    return {
      items: [
        {
          title: 'Films',
          icon: 'mdi-movie',
        },
        {
          title: 'Serials',
          icon: 'mdi-video',
        },
        {
          title: 'TV-shows',
          icon: 'mdi-television-box',
        },
      ],
    };
  },
};
</script>

<style scoped>

</style>
