<template>
  <v-container>
    <h2>Lista de productes</h2>
    <br />
    <v-row>
      <v-col flex v-for="p in productsVue" :key="p.id">
        <v-card class="mx-auto" max-width="300">
          <v-img
            height="150px"
            :src="p.thumbnail"
            gradient="to bottom, rgba(0,0,0,.1), rgba(0,0,0,.5)"
          >
        </v-img>
        <v-card-title v-text="p.title" style="color:yellowgreen"></v-card-title>
          <v-card-text
            class="text--primary"
            v-text="p.description"
          ></v-card-text>
          <v-card-actions>
            <v-btn color="blue" :to="'/producte/' + p.id"> Explore </v-btn>
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      productsVue: [],
    };
  },
  mounted() {
    this.descarregarProductes();
  },
  methods: {
    descarregarProductes() {
      console.log("Provant api..");
      let self = this;
      this.$axios
        .get("https://dummyjson.com/products")
        // Quan acabi
        .then((resposta) => {
          console.log("M'he descarregat les dades bé", resposta.data);
          self.productsVue = resposta.data.products;
        })
        // Si hi ha errors
        .catch((error) => {
          console.log("M'he descarregat les dades malament", error);
        });
    },
  },
};
</script>
