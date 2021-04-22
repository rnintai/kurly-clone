<template>
  <div class="Product view">
    {{ this.$route.params.category }}
  </div>
</template>

<script>
  export default {
    name: "Product"
  };
</script>

<style lang="scss" scoped>
  .Product {
  }
</style>
