<template>
  <v-container>
    <v-row>
      <v-col>
        <v-card
          class="product-card mx-auto"
          @mouseover="showDetails = true"
          @mouseleave="showDetails = false"
          max-width="1000px"
        >
          <v-img aspect-ratio="1.75" :src="producteVue.thumbnail"></v-img>
          <div class="product-info" v-if="showDetails">
            <v-card-title
              v-text="producteVue.title"
              style="color: #2f7693"
            ></v-card-title>
            <v-card-title
              v-text="producteVue.price + ' $'"
              style="color: #708083"
            ></v-card-title>
            <v-rating
              :value="producteVue.rating"
              color="amber"
              dense
              half-increments
              readonly
              size="14"
            ></v-rating>
            <div class="grey--text ms-4"></div>
            <v-card-text
              class="text--primary"
              v-text="producteVue.description"
            ></v-card-text>
            <v-card-text
              class="text--primary"
              v-text="producteVue.category"
            ></v-card-text>
            <v-card-actions>
              <v-btn color="primary" :to="'/'"> Home </v-btn>
            </v-card-actions>
          </div>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  mounted() {
    this.descarregarProducte();
  },
  methods: {
    descarregarProducte() {
      let id = this.$route.params.idProducte;
      let self = this;
      console.log(id);
      this.$axios
        .get(`https://dummyjson.com/products/${id}`)
        .then((response) => {
          self.producteVue = response.data;
          console.log(self.producteVue);
        })
        .catch((error) => {
          console.log(error);
        });
    },
  },
  data() {
    return {
      producteVue: {},
      showDetails: false,
    };
  },
};
</script>

<style scoped>
.product-card {
  position: relative;
  transition: all 0.2s ease-in-out;
}

.product-card:hover .product-info {
  opacity: 1;
  visibility: visible;
}

.product-info {
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  background: rgba(255, 255, 255, 0.9);
  padding: 1rem;
  visibility: hidden;
  opacity: 0;
  transition: all 0.2s ease-in-out;
}
</style>
