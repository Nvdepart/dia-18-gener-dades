<template>
  <div>
    <Landing />
    <SlideProducts :products="productsIn" />
  </div>
</template>

<script>
export default {
  async created() {
    await this.$axios
      .get("https://dummyjson.com/products")
      // Quan acabi
      .then((resposta) => {
        console.log("M'he descarregat les dades bé", resposta.data);
        this.productsIn = resposta.data.products;
        console.log("Opp", this.productsIn);
      });
  },
  data() {
    return {
      productsIn: [],
    };
  },
};
</script>

<style scoped></style>
