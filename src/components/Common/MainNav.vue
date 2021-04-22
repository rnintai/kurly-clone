<template>
  <nav class="MainNav">
    <div class="nav-header">
      <a href="#" class="ad-link">
        <span>수도권 이외 지역</span>
        <strong class="kurly-active-text">택배배송 ></strong>
      </a>
      <ul class="header-link-list">
        <li class="link-list-item">
          <a href="" class="kurly-active-text">회원가입</a>
        </li>
        <li class="link-list-item">
          <a href="">로그인</a>
        </li>
        <li class="link-list-item">
          <a href="">고객센터</a>
        </li>
      </ul>
    </div>
    <!--  -->
    <div class="nav-body">
      <router-link to="/" class="main-logo-wrap">
        <img
          class="main-logo"
          src="https://res.kurly.com/images/marketkurly/logo/logo_x2.png"
          alt=""
        />
      </router-link>
    </div>
    <!--  -->
    <div class="nav-list">
      <a
        href=""
        class="nav-category"
        @mouseenter="is_category_hover = true"
        @mouseleave="is_category_hover = false"
      >
        <img :src="computed_src" alt="햄버거 메뉴 아이콘" />
        <span class="text-category">전체 카테고리</span>
      </a>
      <ul class="nav-category-list">
        <li class="category-item">
          <router-link to="/product/new" class="category-link"
            >신상품</router-link
          >
        </li>
        <li class="category-item">
          <router-link to="/product/best" class="category-link"
            >베스트</router-link
          >
        </li>
        <li class="category-item">
          <router-link to="/" class="category-link">알뜰쇼핑</router-link>
        </li>
        <li class="category-item">
          <router-link to="/" class="category-link">금주혜택</router-link>
        </li>
      </ul>
      <div class="nav-search-and-icons">
        <div class="search-box">
          <input class="search-input" type="text" />
          <a href="" class="search-btn">
            <img
              class="search-ico"
              src="https://res.kurly.com/pc/service/common/1908/ico_search_x2.png"
              alt=""
            />
          </a>
        </div>
        <ul class="icon-list">
          <li id="cart-icon" class="icon-item">
            <img
              src="https://res.kurly.com/pc/ico/2008/ico_delivery_setting.svg?ver=1"
              alt=""
            />
          </li>
          <li class="icon-item">
            <img
              src="https://res.kurly.com/pc/service/common/2011/ico_cart.svg"
              alt=""
            />
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>

<script>
  export default {
    name: "MainNav",
    data: () => ({
      is_category_hover: false
    }),
    computed: {
      computed_src() {
        return this.is_category_hover
          ? "https://res.kurly.com/pc/service/common/1908/ico_gnb_all.png"
          : "https://res.kurly.com/pc/service/common/1908/ico_gnb_all_off.png";
      }
    },
    methods: {}
  };
</script>

<style lang="scss" scoped>
  .MainNav {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    padding: 0 100px;
    z-index: 9;
    background-color: #fff;
    box-shadow: 0 1px 6px 0 rgba(32, 33, 36, 0.28);
    .nav-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      height: 37px;
      //   border-bottom: 1px solid;
      .ad-link {
        padding: 5px 7px;
        font-size: 10px;
        border: 1px solid grey;
        border-radius: 40px;
        color: grey;
        .kurly-active-text {
          display: inline-block;
          margin-left: 5px;
          font-weight: 700;
        }
      }
      .header-link-list {
        font-size: 12px;
        .link-list-item {
          display: inline-block;
          padding: 0 11px;
          & + .link-list-item {
            border-left: 1px solid grey;
          }
        }
      }
    }
    .nav-body {
      position: relative;
      height: 63px;
      .main-logo-wrap {
        position: absolute;
        display: block;
        left: 50%;
        transform: translateX(-50%);
        bottom: 6px;
        width: 103px;
        height: 79px;

        .main-logo {
          width: 100%;
          height: 100%;
        }
      }
    }
    .nav-list {
      display: flex;
      justify-content: space-between;
      align-items: center;
      height: 55px;
      font-weight: 700;
      .nav-category {
        .text-category {
          margin-left: 10px;
        }
        &:hover {
          color: #5f0080;
        }
      }
      .nav-category-list {
        .category-item {
          padding: 0 30px;
          display: inline-block;
          .router-link-exact-active {
            color: #5f0080;
          }
          &:hover {
            .category-link {
              color: #5f0080;
              border-bottom: 1px solid #5f0080;
              //   text-decoration: underline;
            }
          }
        }
      }
      .nav-search-and-icons {
        display: flex;

        .search-box {
          display: flex;
          align-items: center;
          padding-left: 14px;
          border: 1px solid #f7f7f6;
          border-radius: 18px;
          background-color: #f7f7f7;

          .search-input {
            background-color: inherit;
          }
          .search-btn {
            display: inline-block;
            width: 30px;
            height: 30px;
            .search-ico {
              width: 100%;
              height: 100%;
            }
          }
        }
        .icon-list {
          #cart-icon {
            padding: 0 15px;
          }
          .icon-item {
            display: inline-block;
          }
        }
      }
    }
  }
</style>
