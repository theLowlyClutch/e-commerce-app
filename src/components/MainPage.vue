<template>
  <div class="main-page">
    Main page from component
    <ProductPanel title="Newest Arrivals" section="newarrivals" />
    <ProductPanel title="Popular" section="popular" />
    <ProductPanel title="Trending" section="trending" />
    <ProductPanel title="Best Deals" section="bestdeals" />
  </div>
</template>


<script>
import ProductPanel from "./ProductPanel.vue";

export default {
  name: "MainPage",
  components: {
    ProductPanel
  }
};
</script>