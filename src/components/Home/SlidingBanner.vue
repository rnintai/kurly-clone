<template>
  <div class="sliding-wrap">
    <ul class="slides">
      <li class="slide-list" v-for="image in images" :key="image">
        <img class="slide-image" :src="image" alt="배너1" />
      </li>
    </ul>
    <button class="prev-btn" @click="prevClick">
      <i class="fas fa-chevron-circle-left"></i>
    </button>
    <button class="next-btn" @click="nextClick">
      <i class="fas fa-chevron-circle-right"></i>
    </button>
  </div>
</template>

<script>
  export default {
    name: "sliding-banner",
    data: () => ({
      images: [
        "https://img-cf.kurly.com/shop/data/main/1/pc_img_1618996028.jpg",
        "https://img-cf.kurly.com/shop/data/main/1/pc_img_1618485461.jpg",
        "https://user-images.githubusercontent.com/65759076/115874178-c4d41500-a47e-11eb-8911-90395b33e669.png"
      ],
      slideWidth: 1581,
      slideMargin: 0,
      currentIdx: 0,
      slideCount: 3
    }),
    methods: {
      prevClick() {
        let cur = this.currentIdx;
        cur = cur - 1;
        cur === -1
          ? (cur = this.slideCount - 1)
          : (cur = cur % this.slideCount);
        var slides = document.querySelector(".slides");
        this.currentIdx = cur;
        this.LmoveSlide(slides, cur);
      },
      nextClick() {
        let cur = this.currentIdx;
        cur = cur + 1;
        cur = cur % this.slideCount;
        this.currentIdx = cur;
        var slides = document.querySelector(".slides");
        this.RmoveSlide(slides, cur);
      },
      RmoveSlide(slides, num) {
        var width = document.querySelector(".slide-image").clientWidth;
        slides.style.left = num * -width + "px";
      },
      LmoveSlide(slides, num) {
        var width = document.querySelector(".slide-image").clientWidth;
        slides.style.left = num * -width + "px";
      }
    }
  };
</script>

<style lang="scss" scoped>
  button {
    border: 0;
    outline: 0;
    cursor: pointer;
    background-color: transparent;
  }
  .sliding-wrap {
    position: relative;
    width: 100%;
    height: 300px;
    margin: 0;
    padding: 0;
    overflow: hidden;
    .slides {
      position: absolute;
      width: 300%;
      height: 300px;
      left: 0;
      transition: left 0.5s ease-in-out;
      .slide-list {
        display: inline-block;
        width: 33.3%;
        .slide-image {
          width: 100%;
          min-width: 1150px;
        }
      }
      // li:not(:last-child) {
      //   float: left;
      //   margin-right: 30px;
      // }
    }
    .prev-btn,
    .next-btn {
      font-size: 150%;
      position: absolute;
      display: inline-block;
      left: 5%;
      transform: translate(-50%, -50%);
      top: 50%;
    }
    .next-btn {
      left: 95%;
    }
    .fa-chevron-circle-left,
    .fa-chevron-circle-right {
      font-size: 200%;
    }
    .fa-chevron-circle-left:hover {
      opacity: 30%;
      transform: translateX(-1.5px);
      transition: all 0.5s;
    }
    .fa-chevron-circle-left:not(hover) {
      opacity: 15%;
      transition: all 0.5s;
    }
    .fa-chevron-circle-right:hover {
      opacity: 30%;
      transform: translateX(1.5px);
      transition: all 0.5s;
    }
    .fa-chevron-circle-right:not(hover) {
      opacity: 15%;
      transition: all 0.5s;
    }
  }
</style>
