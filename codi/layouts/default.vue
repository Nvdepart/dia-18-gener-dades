<template>
  <v-app dark>
    <NavBar />
    <v-main>
      <v-container>
        <Nuxt />
        <Scroll />
      </v-container>
    </v-main>
    <v-footer>
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  name: "DefaultLayout",
};
</script>
