<template>
  <div class="product-card-frame">
    <div class="product-card" v-for="product in product_data" :key="product.id">
      <div class="product-wrapper">
        <a href="">
          <img
            :src="product.thumb"
            alt="상품 썸네일"
            class="product-card-thumb"
          />
        </a>
      </div>
      <div class="product-content">
        <span class="product-name">{{ product.name }}</span>
        <span class="product-cost">{{ product.cost }}원</span>
        <span class="product-desc">{{ product.desc }}</span>
      </div>
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
      padding: 0 39px;
      .product-wrapper {
        width: 250px;
        height: 322px;
        overflow: hidden;
        margin-bottom: 10px;
        .product-card-thumb {
          width: 100%;
        }
        &:hover {
          .product-card-thumb {
            transform: scale(1.03);
            transition: all 0.3s ease-in-out;
          }
        }
        &:not(:hover) {
          .product-card-thumb {
            transition: all 0.3s ease-in-out;
          }
        }
      }
      .product-content {
        .product-name {
          display: block;
          height: 45px;
        }
        .product-cost {
          display: block;
          padding: 5px 0 0 0;
          font-weight: 700;
        }
        height: 40px;
        .product-desc {
          display: block;
          padding: 5px 0 0 0;
          font-size: 12px;
          color: #c5c5c5;
        }
      }
    }
  }
</style>
