<template>
  <div>
    <Landing />
    <SlideProducts :products="products" />
  </div>
</template>

<script>
export default {
  async created() {
    this.products = await this.$axios
      .get("https://dummyjson.com/products")
      // Quan acabi
      .then((resposta) => {
        console.log("M'he descarregat les dades bé", resposta.data);
        self.products = resposta.data.products;
        console.log(products);
      });
  },
  data() {
    return {
      products: [],
    };
  },
};
</script>

<style scoped></style>
