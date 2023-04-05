<template>
  <v-container class="home">
    <v-card
      flat
      class="px-3"
      :key="item.title"
      v-for="item in projects"
    >
      <v-layout row wrap :class="`py-4 project ${item.status}`">
        <v-flex xs12 md6 class="px-4">
          <div class="caption grey--text">Project title</div>
          <div> {{ item.title }} </div>
        </v-flex>
        <v-flex xs6 sm4 md2>
          <div class="caption grey--text">Person</div>
          <div> {{ item.person }} </div>
        </v-flex>
        <v-flex xs6 sm4 md2>
          <div class="caption grey--text">Date</div>
          <div> {{ item.date }} </div>
        </v-flex>
        <v-flex xs2 sm4 md2>
          <div>
            <v-chip small :class="`${item.status} white--text caption my-2`">
              {{ item.status }}
            </v-chip>
          </div>
        </v-flex>
        <v-divider></v-divider>
      </v-layout>
    </v-card>
  </v-container>
</template>

<script>
export default {
  name: 'HomePage',
  data() {
    return {
      projects: [
        {
          title: 1,
          person: 1,
          date: 1,
          status: 'on',
        },
        {
          title: 2,
          person: 2,
          date: 2,
          status: 'off',
        },
        {
          title: 3,
          person: 3,
          date: 3,
          status: 'err',
        },
      ],
    };
  },
};
</script>

<style scoped>
  .project.on {
    border-left: 4px solid green;
  }

  .project.off {
    border-left: 4px solid orange;
  }

  .project.err {
    border-left: 4px solid tomato;
  }
  .v-chip.on {
    background: green;
  }
  .v-chip.off {
    background: orange;
  }
  .v-chip.err{
    background: tomato;
  }
</style>
