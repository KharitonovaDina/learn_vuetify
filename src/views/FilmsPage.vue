<template>
  <v-container class="films">
    <v-snackbar v-model="snackbar" :timeout="4000" top color="success">
      <span>Welcome!</span>
      <template v-slot:action="{ attrs }">
        <v-btn
          color="white"
          text
          v-bind="attrs"
          @click="snackbar = false"
        >
          Close
        </v-btn>
      </template>
    </v-snackbar>
    <v-dialog
      v-model="dialog"
      width="500"
    >
      <template v-slot:activator="{ on, attrs }">
        <v-btn
          elevation="0"
          color="red"
          class="white--text"
          v-bind="attrs"
          v-on="on"
        >
          Add new project
        </v-btn>
      </template>
      <v-card>
        <v-card-title>
          New project
        </v-card-title>
        <v-card-text>
          <v-form ref="form">
            <v-text-field
              label="Text"
              v-model="text"
              prepend-icon="mdi-folder"
              :rules="inputRules"
            >
            </v-text-field>
            <v-textarea
              label="Information"
              v-model="info"
              prepend-icon="mdi-pencil"
              :rules="inputRules"
            >
            </v-textarea>
            <v-menu
              v-model="menu"
              max-width="290"
            >
              <template v-slot:activator="{ on, attrs }">
                <v-text-field
                  :value="formattedDate"
                  label="Date"
                  v-bind="attrs"
                  v-on="on"
                  prepend-icon="mdi-calendar-range"
                  :rules="inputRules"
                ></v-text-field>
              </template>
              <v-date-picker
                v-model="date"
                @change="menu = false"
              ></v-date-picker>
            </v-menu>

            <v-btn
              elevation="0"
              class="success mx-0 mt-3"
              @click="submit"
            >
              Add project
            </v-btn>
          </v-form>
        </v-card-text>
      </v-card>
    </v-dialog>
  </v-container>
</template>

<script>
// eslint-disable-next-line import/no-extraneous-dependencies
import { format, parseISO } from 'date-fns';

export default {
  name: 'FilmsPage',
  data() {
    return {
      text: '',
      info: '',
      date: '',
      menu: false,
      inputRules: [
        (v) => v.length >= 3 || 'Minimum length is 3 characters',
      ],
      dialog: false,
      snackbar: false,
    };
  },

  methods: {
    submit() {
      if (this.$refs.form.validate()) {
        this.dialog = false;
        this.snackbar = true;
      }
    },
  },

  computed: {
    formattedDate() {
      return this.date ? format(parseISO(this.date), 'do MMMM yyyy') : '';
    },
  },
};
</script>

<style scoped>

</style>
