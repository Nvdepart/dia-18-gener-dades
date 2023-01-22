<template>
  <div>
    <pre>{{ products }}</pre>
    hh

    <v-slide-group>
      <v-col v-for="p in products" :key="p.id" color="blue" width="300">
        <h1>Hola1</h1>
        <v-card
          nuxt
          :to="`/products/${p.id}`"
          color="surface"
          width="300"
          class="el ma-2 mb-5 mr-5"
        >
          <v-img :src="p.thumbnail" height="300">
            <template #placeholder>
              <v-row class="fill-height" justify="center" align="center">
                <v-progress-circular
                  width="2"
                  size="100"
                  color="primary"
                  indeterminate
                ></v-progress-circular>
              </v-row>
            </template>
          </v-img>
          <v-card-title class="text-md-body-1 font-weight-bold">
            {{ p.title }}
            <h2>holla</h2>
          </v-card-title>
        </v-card>
      </v-col>
    </v-slide-group>
    <p>Je suis ici</p>
  </div>
</template>

<script>
export default {
  props: {
    products: Array,
  },
};
</script>

<style lang="scss" scoped></style>
