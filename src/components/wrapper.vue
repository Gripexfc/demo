<template>
    <div class="page-home-wrapper">
      <el-carousel indicator-position="outside" arrow='never' @change="carousel" ref="carouselSwich">
        <el-carousel-item v-for="item in state.wrapperList" :key="item" id="carousel">
          <img class="slide-imgwrap-pic" :src="item" alt="">
        </el-carousel-item>
      </el-carousel>
      <div class="slide-nav">
        <img @click="swipperClick('prev')" src="../assets/prev.png" style="width: 20px; height: 20px;" alt="">
        <ul class="slide-nav-list">
          <li v-for="item in state.carouselList" :key="item" class="slide-nav-item">
            <a @click="slideClick(item)" href="javascript:void(0)" class="slide-nav-item-link">{{ item.title }}</a>
            <p v-show="state.carouselIndex === item.id" style="background: #009cff; height: 6px;width: 100%;position: absolute; bottom: 0;"></p>
          </li>
        </ul>
      <img @click="swipperClick('next')" src="../assets/next.png" style="width: 20px; height: 20px;" alt="">
      </div>
    </div>
</template>

<script setup>
  import {reactive, ref} from 'vue';

  const carouselSwich = ref(null);
  const state = reactive({
    carouselList: [
      {
        id: 0,
        title: '第四届追梦营'
      },
      {
        id: 1,
        title: '深圳创客节创意编程赛'
      },
      {
        id: 2,
        title: '深圳TGE虚拟机器人挑战赛'
      },
      {
        id: 3,
        title: '编程与人工智能活动'
      },
      {
        id: 4,
        title: '腾讯游戏年度故事片'
      },
    ],
    wrapperList: [
      'https://wuji-30130.sz.gfp.tencent-cloud.com/pics/20211230_u9kh06gxj4a79e15a997c42203c515773168a900f9.jpg',
      'https://wuji-30130.sz.gfp.tencent-cloud.com/pics/20221017_i1n62bthmuobanner.png',
      'https://wuji-30130.sz.gfp.tencent-cloud.com/pics/20220901_rz0z7qqh2gtgebanner.jpg',
      'https://wuji-30130.sz.gfp.tencent-cloud.com/pics/20220909_9e0choci7rg_20220909101245.jpg',
      'https://wuji-30130.sz.gfp.tencent-cloud.com/pics/20211230_u9kh06gxj4a79e15a997c42203c515773168a900f9.jpg'

    ],
    carouselIndex: 0,
  })

  const carousel = (index) => {
    state.carouselIndex = index;
  }

  const swipperClick = (to) => {
    if (to === 'next') {
      carouselSwich.value.next()
    } else {
      carouselSwich.value.prev()
    }
  }

  const slideClick = (item) => {
    carouselSwich.value.setActiveItem(item.id)
  }

</script>

<style lang='less'>
.page-home-wrapper {
  position: relative;

  .slide-nav {
    position: absolute;
    width: 1200px;
    left: 50%;
    bottom: 0;
    margin-left: -600px;
    height: 50px;
    background: rgba(255, 255, 255, 0.8);
    border-radius: 12px 12px 0 0;
    overflow: hidden;
    z-index: 9;
    display: -webkit-box;
    display: -webkit-flex;
    display: -ms-flexbox;
    display: flex;
    -webkit-box-orient: horizontal;
    -webkit-box-direction: normal;
    -webkit-flex-flow: row wrap;
    -ms-flex-flow: row wrap;
    flex-flow: row wrap;
    -webkit-box-align: center;
    -webkit-align-items: center;
    -ms-flex-align: center;
    align-items: center;

    .slide-nav-btn.prev {
      border-right: 1px solid rgba(255, 255, 255, 0.6);
    }

    .slide-nav-list {
      flex: 1;
      height: 50px;
      display: -webkit-box;
      display: -webkit-flex;
      display: -ms-flexbox;
      display: flex;
      -webkit-box-orient: horizontal;
      -webkit-box-direction: normal;
      -webkit-flex-flow: row wrap;
      -ms-flex-flow: row wrap;
      flex-flow: row wrap;
      -webkit-box-align: center;
      -webkit-align-items: center;
      -ms-flex-align: center;
      align-items: center;
      .slide-nav-item {
        flex: 1;
        text-align: center;
        position: relative;
        line-height: 50px;
        border-right: 1px solid rgba(255, 255, 255, 0.6);
        .slide-nav-item-link:hover {
          color: #009cff;
        }
        .slide-nav-item-link {
          display: block;
          color: #4a596f;
          font-size: 16px;
          transition: all 200ms;
        }
      }
    }

    .slide-nav-btn::after {
      content: '';
      position: absolute;
      left: 0;
      bottom: 0;
      height: 6px;
      width: 100%;
      background: linear-gradient(rgba(255, 255, 255, 0), rgba(0, 0, 0, 0.1));
    }

    .slide-nav-btn {
      display: block;
      width: 50px;
      line-height: 50px;
      text-align: center;
      position: relative;
      font-size: 16px;
      color: rgba(74, 89, 111, 0.4);
    }
  }
}
</style>