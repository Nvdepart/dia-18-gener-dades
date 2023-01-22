<template>
  <v-app-bar app>
    <v-toolbar-title>Atlas-Expo</v-toolbar-title>
    <v-spacer></v-spacer>
    <v-btn text nuxt to="/">
      <v-icon>mdi-home</v-icon>
      Accueil
    </v-btn>
    <v-btn text nuxt to="/products">Produits</v-btn>
    <v-btn text nuxt to="/">Contact</v-btn>
    <v-btn text nuxt to="/">Panier</v-btn>
    <v-btn text> </v-btn>
  </v-app-bar>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped></style>
