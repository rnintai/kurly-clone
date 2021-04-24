<template>
  <div class="product-card-frame">
    <div class="product-card" v-for="product in product_data" :key="product.id">
      <img :src="product.thumb" alt="상품 썸네일" class="product-card-thumb" />
      <span class="product-name">{{ product.name }}</span>
      <span class="product-cost">{{ product.cost }}원</span>
      <span class="product-desc">{{ product.desc }}</span>
    </div>
  </div>
</template>

<script>
  import {
    NewProduct,
    BestProduct
  } from "@/assets/database/product/product.js";

  export default {
    name: "product-card",
    data: () => ({}),
    computed: {
      route() {
        return this.$route.params.category;
      },
      product_data() {
        if (this.route == "new") return NewProduct;
        else return BestProduct;
      }
    }
  };
</script>

<style lang="scss" scoped>
  .product-card-frame {
    position: relative;
    max-width: 1600px;
    min-width: 1000px;
    padding: 20px 100px 0 100px;
    .product-card {
      display: inline-block;
      position: relative;
      width: 250px;
      height: 450px;
      margin: 0 39px;
      .product-card-thumb {
        width: 100%;
        margin-bottom: 10px;
      }
      .product-name {
        display: block;
        height: 45px;
      }
      .product-cost {
        display: block;
        padding: 5px 0 0 0;
        font-weight: 700;
      }
      .product-desc {
        display: block;
        padding: 5px 0 0 0;
        font-size: 12px;
        color: #c5c5c5;
      }
    }
  }
</style>
