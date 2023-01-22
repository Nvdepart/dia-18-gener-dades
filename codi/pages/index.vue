<template>
  <div>
    <Landing :prod="products" />
    <SlideProducts />
  </div>
</template>

<script>
export default {
  props: {
    products: "prod",
  },
};
</script>

<style scoped></style>
