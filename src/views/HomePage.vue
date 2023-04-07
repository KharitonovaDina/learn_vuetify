<template>
  <v-container class="home">
    <v-layout row class="my-3 px-4">
      <v-tooltip top>
        <template v-slot:activator="{ on, attrs }">
          <v-btn
            small
            text
            color="dark-grey"
            @click="sortBy('title')"
            v-bind="attrs"
            v-on="on"
          >
            <v-icon left small>mdi-folder</v-icon>
            <span class="caption text-lowercase">By title</span>
          </v-btn>
        </template>
        <span>Sort project by project name</span>
      </v-tooltip>

      <v-tooltip top>
        <template v-slot:activator="{ on, attrs }">
          <v-btn
            small
            text
            color="dark-grey"
            @click="sortBy('person')"
            v-bind="attrs"
            v-on="on"
          >
            <v-icon left small>mdi-account</v-icon>
            <span class="caption text-lowercase">By person</span>
          </v-btn>
        </template>
        <span>Sort project by person</span>
      </v-tooltip>
      <v-expansion-panels flat class="mb-8">
        <v-expansion-panel
          v-for="item in myProjects"
          :key="item.title"
        >
          <v-expansion-panel-header>
            {{ item.title }}
          </v-expansion-panel-header>
          <v-expansion-panel-content>
            <p>
              {{ item.person + item.date + item.status }}
            </p>
          </v-expansion-panel-content>
        </v-expansion-panel>
      </v-expansion-panels>
    </v-layout>

    <v-card
      flat
      class="pa-3"
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
          title: '5',
          person: '56',
          date: '1',
          status: 'on',
        },
        {
          title: '6',
          person: '8',
          date: '2',
          status: 'off',
        },
        {
          title: '3',
          person: '45',
          date: '3',
          status: 'err',
        },
        {
          title: '36',
          person: '45',
          date: '3',
          status: 'on',
        },
        {
          title: '24',
          person: '45',
          date: '3',
          status: 'off',
        },
      ],
    };
  },

  methods: {
    sortBy(prop) {
      this.projects.sort((a, b) => (a[prop] < b[prop] ? -1 : 1));
    },
  },

  computed: {
    myProjects() {
      return this.projects.filter((project) => (project.person === '45'));
    },
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
