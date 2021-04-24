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
      <div class="nav-dropdown">
        <a
          href="#none"
          class="nav-dropdown-btn"
          @mouseenter="is_category_hover = true"
          @mouseleave="is_category_hover = false"
        >
          <div class="nav-dropdown-btn-content">
            <i class="fas fa-bars"></i>
            <span class="dropdown-btn-text">전체 카테고리</span>
          </div>
        </a>
        <div class="nav-dropdown-content">
          <a
            href="#none"
            class="nav-dropdown-content-wrapper"
            v-for="category in categories"
            :key="category.name"
          >
            <div class="content-item">
              <i :class="category.ico"></i>
              <span class="item-type">{{ category.name }}</span>
            </div>
          </a>
        </div>
      </div>
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
          <router-link to="/product/al" class="category-link"
            >알뜰쇼핑</router-link
          >
        </li>
        <li class="category-item">
          <router-link to="/product/week" class="category-link"
            >금주혜택</router-link
          >
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
          <li class="icon-location">
            <button class="icon-location-button"></button>
            <div class="no-address">
              <span class="emph">배송지를 등록</span>하고<br />
              구매 가능한 상품을 확인하세요!
              <div class="no-address-buttons">
                <button class="no-address-login">로그인</button>
                <button class="no-address-search">주소 검색</button>
              </div>
            </div>
          </li>
          <li class="icon-cart">
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
      is_category_hover: false,
      categories: [
        { name: "채소", ico: "fas fa-seedling" },
        { name: "과일·견과·쌀", ico: "fas fa-apple-alt" },
        { name: "수산", ico: "fas fa-fish" },
        { name: "정육", ico: "fas fa-drumstick-bite" },
        { name: "기타", ico: "fas fa-ellipsis-h" }
      ]
    })
  };
</script>

<style lang="scss" scoped>
  .MainNav {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    z-index: 9;
    padding: 0 100px;
    background-color: #fff;
    box-shadow: 0 0px 22px 0 rgba(0, 0, 0, 0.2);
    .nav-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      width: 1050px;
      height: 37px;
      margin: 0 auto;
      //   border-bottom: 1px solid;
      .ad-link {
        padding: 3px 5px;
        font-size: 11px;
        border: 1px solid #d1d1d1;
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
      width: 1050px;
      height: 63px;
      margin: 0 auto;
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
      width: 1050px;
      height: 55px;
      margin: 0 auto;
      font-weight: 700;
      .nav-dropdown {
        position: relative;
        display: inline-block;
        height: 55px;
        .nav-dropdown-btn {
          &:hover {
            color: var(--kurly-color);
          }
          .nav-dropdown-btn-content {
            position: relative;
            top: 30%;
            .dropdown-btn-text {
              width: 100%;
              height: 100%;
              margin: 0 34px 0px 12px;
            }
          }
        }
        .nav-dropdown-content {
          display: none;
          position: absolute;
          top: 55px;
          min-width: 160px;
          background-color: #fff;
          box-shadow: 0px 8px 16px 0px rgba(0, 0, 0, 0.2);
          border-radius: 5px;

          .nav-dropdown-content-wrapper {
            padding: 12px 12px;
            // margin: 15px;
            display: flex;
            flex-direction: column;
            .content-item {
              display: flex;
              justify-content: space-between;
              // margin: 8px 12px 8px 12px;
              width: 100%;
              i {
                width: 20%;
              }
              .item-type {
                // margin-left: 15px;
                width: 80%;
                font-weight: 300;
              }
            }
            &:hover {
              background-color: #f5f5f5;
              color: var(--kurly-color);
            }
          }
        }
        &:hover {
          .nav-dropdown-content {
            display: block;
          }
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
        align-items: center;
        .search-box {
          display: flex;
          align-items: center;
          padding-left: 14px;
          height: 50%;
          border: 1px solid #f7f7f6;
          border-radius: 18px;
          background-color: #f7f7f7;
          .search-input {
            background-color: inherit;
            line-height: 2em;
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
          .icon-location {
            display: inline-block;
            padding: 15px 15px;
            .icon-location-button {
              width: 36px;
              height: 36px;
              background-image: url("https://res.kurly.com/pc/ico/2008/ico_delivery_setting.svg?ver=1");
            }

            &:hover {
              .icon-location-button {
                background-image: url("https://res.kurly.com/pc/ico/2010/ico_delivery_setting_on.svg");
              }
              .no-address {
                display: block;
              }
            }
            .no-address {
              display: none;
              position: absolute;
              top: 155px;
              right: 291px;
              width: 250px;
              padding: 20px 18px;
              border: 1px solid #ddd;
              background-color: #fff;
              .emph {
                font-weight: 600;
                color: var(--kurly-color);
              }
              .no-address-buttons {
                display: flex;
                justify-content: space-between;
                margin-top: 17px;
                .no-address-login,
                .no-address-search {
                  padding: 10px 25px;
                  border: 1px solid var(--kurly-color);
                  border-radius: 3px;
                  cursor: pointer;
                }
                .no-address-login {
                  color: var(--kurly-color);
                  width: 40%;
                }
                .no-address-search {
                  margin-left: 10px;
                  width: 60%;
                  background-color: var(--kurly-color);
                  color: #fff;
                }
              }
            }
          }
          .icon-cart {
            display: inline-block;
          }
        }
      }
    }
  }
</style>
