<template>
  <v-app-bar app absolute flat dense tile class="px-16">
    <v-tabs hide-slider>
      <v-tab nuxt to="/">Accueil</v-tab>
      <v-tab nuxt to="/article">Exemple d'article</v-tab>
      <v-tab>Item Three</v-tab>
    </v-tabs>
    <v-spacer></v-spacer>
    <v-btn icon tile>
      <v-icon> mdi-github </v-icon>
    </v-btn>
    <v-btn icon tile @click="toggleTheme">
      <v-icon> mdi-theme-light-dark </v-icon>
    </v-btn>
    <v-btn icon tile>
      <v-icon> mdi-bell </v-icon>
    </v-btn>
    <MenuProfile />
  </v-app-bar>
</template>

<script>
import MenuProfile from '~/components/Header/Bar/MenuProfile.vue'
export default {
  name: 'AppBar',
  components: { MenuProfile },
  methods: {
    toggleTheme() {
      this.$vuetify.theme.dark = !this.$vuetify.theme.dark
      localStorage.setItem('useDarkTheme', this.$vuetify.theme.dark.toString())
    },
  },
}
</script>

<style>
.v-toolbar__content {
  padding-bottom: 0px !important;
  padding-top: 0px !important;
}
</style>
