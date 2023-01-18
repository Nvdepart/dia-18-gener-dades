<template>
  <v-container>
    <h2>Lista de productes</h2>
    <v-row>
      <v-card cols="3" v-for="(p,i) in productsVue" :key="p.id">
          <v-img max-width="200px" :src="p.thumbnail"></v-img>
          <v-card-title>{{p.title}}</v-card-title>
          <v-card-text>{{p.description}}</v-card-text>
      </v-card>
    </v-row>
  </v-container>
</template>

<script>
export default {
  data(){
      return {
        productsVue:null,
      }
    },
  mounted(){
        this.descarregarProductes()
      },
  methods:{
    descarregarProductes(){
      console.log('Provant api..')
      let self = this
      this.$axios.get('https://dummyjson.com/products')
        // Quan acabi
        .then(
          resposta=>{
            console.log("M'he descarregat les dades bé",resposta.data)
            self.productsVue = resposta.data.products
            
          }
        )
        // Si hi ha errors
        .catch(
          error=>{
            console.log("M'he descarregat les dades malament",error)
          }
        )
    },
    
  }
}
</script>
