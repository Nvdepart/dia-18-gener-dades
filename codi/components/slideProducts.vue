<template>
  <div>
    <v-slide-group>
      <v-col v-for="p in products" :key="p.id" color="blue" width="300">
        <v-card
          nuxt
          :to="`/producte/${p.id}`"
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
          </v-card-title>
        </v-card>
      </v-col>
    </v-slide-group>
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
