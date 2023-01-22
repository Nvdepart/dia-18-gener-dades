<template>
  <v-btn v-if="showScrollBtn" @click="scrollToTop" class="scroll-to-top">
    <v-icon>arrow_upward</v-icon>
  </v-btn>
</template>
<script>
export default {
  data: () => ({
    showScrollBtn: false,
  }),
  created() {
    window.addEventListener("scroll", this.handleScroll);
  },
  beforeDestroy() {
    window.removeEventListener("scroll", this.handleScroll);
  },
  methods: {
    scrollToTop() {
      window.scrollTo({ top: 0, behavior: "smooth" });
    },
  },
};
</script>
