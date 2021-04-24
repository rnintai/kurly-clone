<template>
  <div class="Product view">
    <product-card></product-card>
  </div>
</template>

<script>
  import ProductCard from "@/components/Common/ProductCard.vue";

  export default {
    name: "Product",
    components: { ProductCard }
  };
</script>

<style lang="scss" scoped></style>
