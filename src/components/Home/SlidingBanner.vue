<template>
  <div class="sliding-wrap">
    <ul class="slides" :style="slides_width">
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
        "https://img-cf.kurly.com/shop/data/main/1/pc_img_1617955868.jpg"
      ],
      slides: document.querySelector(".slides"),
      slide: document.querySelectorAll(".slides .slide-list"),
      slideWidth: 1920,
      slideMargin: 30,
      currentIdx: 0,
      slideCount: 3,
      prevBtn: document.querySelector(".prev-btn"),
      nextBtn: document.querySelector(".next-btn")
    }),
    computed: {
      slides_width() {
        var width =
          (this.slideWidth + this.slideMargin) * this.slideCount -
          this.slideMargin;
        return "width: " + width + "px";
      }
    },
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
        slides.style.left = num * (-this.slideWidth - this.slideMargin) + "px";
      },
      LmoveSlide(slides, num) {
        slides.style.left = num * (-this.slideWidth + -this.slideMargin) + "px";
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
    width: 1920px;
    height: 374px;
    margin: 0;
    padding: 0;
    overflow: hidden;
    .slides {
      position: absolute;
      left: 0;
      transition: left 0.5s ease-in-out;
      .slide-list {
        .slide-image {
          width: 1920px;
        }
      }
      li:not(:last-child) {
        float: left;
        margin-right: 30px;
      }
    }
    .prev-btn,
    .next-btn {
      position: absolute;
      display: inline-block;
      left: 15%;
      transform: translate(-50%, -50%);
      top: 50%;
    }
    .next-btn {
      left: 85%;
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
