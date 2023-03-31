<template>
  <v-container class="navbar">
    <v-navigation-drawer
      class="navbar__wrap"
      tag="nav"
    >
      <div class="navbar__logo">
        <span class="navbar__logo-txt"> Filmoteka </span>
      </div>
      <v-list
        class="pa-0"
        dark
        nav
      >
        <v-list-item
          v-for="item in items"
          :key="item.title"
          class="pa-0"
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
    <PrimaryBtn
      class="navbar__login-btn"
    />
  </v-container>
</template>

<script>
import PrimaryBtn from '@/components/PrimaryBtn.vue';

export default {
  name: 'NavBar',
  components: { PrimaryBtn },
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
  .navbar {
    display: flex;
    flex-direction: column;
    height: 100vh;
    width: 235px;
    padding: 36px 24px;
    margin: 0;
    background-color: #1E1717;
  }
  .navbar__wrap {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    background-color: inherit;
    border: none;
  }
  .navbar__logo{
    margin-bottom: 24px;
  }
  .navbar__logo-txt {
    color: white;
    text-transform: uppercase;
    font-size: 32px;
    font-weight: 700;
  }
  .navbar__login-btn {
    width: 100%;
    color: white;
  }
</style>
