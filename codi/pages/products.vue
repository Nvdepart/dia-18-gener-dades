<template>
    <v-container>
      <div>
        <v-row>
          <v-col cols="6">
            <v-text-field
              v-model="search"
              rounded
              outlined
              width="150px"
              label="Buscar Producte"
            ></v-text-field>
          </v-col>
          <v-col cols="6">
            <v-select 
            v-model="selectedCategory" 
            :items="categoriesVue"
            clearable
            ></v-select>
          </v-col>
        </v-row>
      </div>
      <hr />
      <br>
      <v-row>
        <v-col flex v-for="p in filteredProducts" :key="p.id">
          <v-card class="mx-auto" max-width="300">
            <v-img
              height="150px"
              :src="p.thumbnail"
              gradient="to bottom, rgba(0,0,0,.1), rgba(0,0,0,.5)"
            >
            </v-img>
            <v-card-title
              v-text="p.title"
              style="color: yellowgreen"
            ></v-card-title>
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
        categoriesVue: [],
        selectedCategory: "all",
        search: "",
      };
    },
    computed: {
      filteredProducts() {
        if (this.selectedCategory === "all") {
          return this.productsVue.filter((product) => {
            return product.title
              .toLowerCase()
              .includes(this.search.toLowerCase());
          });
        }
        console.log(this.selectedCategory);
        return this.productsVue.filter((p) => {
          return p.category === this.selectedCategory
           ;
        }
         
        );
      },
    },
    mounted() {
      this.descarregarProductes();
      this.descarregarGategories();
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
      descarregarGategories() {
        let self = this;
        this.$axios
          .get("https://dummyjson.com/products/categories")
          // Quan acabi
          .then((res) => {
            console.log("M'he descarregat les gategories bé", res);
            self.categoriesVue = res.data;
          })
          // Si hi ha errors
          .catch((error) => {
            console.log("M'he descarregat les dades malament", error);
          });
      },
    },
  };
  </script>
  