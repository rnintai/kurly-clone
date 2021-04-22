<template>
  <div class="sliding-banner">
    <img
      class="sliding-image"
      src="https://img-cf.kurly.com/shop/data/main/1/pc_img_1618996028.jpg"
      alt="배너1"
    />
  </div>
</template>

<script>
  export default {
    name: "sliding-banner"
  };
</script>

<style lang="scss" scoped>
  .sliding-banner {
    height: 370px;
    .sliding-image {
      width: 100%;
      height: 100%;
    }
  }
</style>
