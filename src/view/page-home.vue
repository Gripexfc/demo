<template>
  <div class='page-home'>
    <!-- 导航栏 -->
    <Head></Head>
    <!-- 轮播图 -->
    <Wrapper></Wrapper>
    <!-- 编程好工具，学习更轻松 -->
    <div class="page-home-inner" id="tool">
      <div class="page-home-panel-hd">
        <h2 class="page-home-panel-title">编程好工具，学习更轻松</h2>
        <p class="page-home-panel-title-info">选择适合你的编程神器</p>
      </div>
      <div class="page-home-panel-bd">
        <div class="labs">
          <div class="labs-aside">
            <ul class="labs-nav">
              <li @click="labsClick(item.id)" class="labs-nav-item" :class="state.toolSelect === item.id ? 'current' : ''" v-for="item in state.toolList" :key="item">
                <div class="labs-nav-item-icon">
                  <img class="labs-nav-item-icon-pic" :src="item.ico" alt="icon">
                </div>
                <div class="labs-nav-item-meta">
                  <p class="labs-nav-item-title">{{ item.title }}</p>
                  <p class="labs-nav-item-info">
                    <span class="labs-nav-item-info-tag">{{ item.describe[0] }}</span>
                    <span class="labs-nav-item-info-tag">{{ item.describe[1] }}</span>
                    <span class="labs-nav-item-info-tag">{{ item.describe[2] }}</span>
                  </p>
                </div>
              </li>
            </ul>
          </div>
          <div class="labs-main">
            <div class="labs-intro">
              <div class="labs-intro-figure">
                <p class="labs-intro-figure-info">
                  <i class="iconhome iconhome-flag"></i>{{ state.toolList[state.toolSelect].content.title }}
                </p><p class="labs-intro-figure-title">{{state.toolList[state.toolSelect].content.text}}</p>
                <p class="labs-intro-figure-description">{{ state.toolList[state.toolSelect].content.bdText }}</p>
                
                <div class="labs-intro-figure-ctrl">
                  <el-button class="labs-intro-figure-ctrl" type="primary" round>立即创作</el-button>
                  <a href="https://coding.qq.com/labs/detail?id=1" style="margin-left: 28px;" class="labs-intro-figure-ctrl-link" target="_blank" rel="noopener noreferrer">了解更多</a>
                </div>

              </div>
              <div class="labs-intro-cover" style="cursor: pointer;"><div id="hzi5wcp6i" class="video-player-wrapper">
                <video id="course-video" class="video-player-enter" :src="state.toolList[state.toolSelect].content.video" autoplay="" playsinline="" webkit-playsinline="true" mtt-playsinline="true" loop="" style="width: 100%; height: 100%;">
                </video>
              </div>
            </div>
            </div>
            <div class="labs-example">
              <div class="labs-example-hd">
                <H3>入门学习</H3>
                <a>更多案例</a>
              </div>
              <div class="labs-example-bd">
                <ul class="labs-example-list">
                  <li class="labs-example-item">
                    <img class="imgwrap-pic" src="https://wuji-30130.sz.gfp.tencent-cloud.com/pics/20200318_7wbr2yla49.png" alt="">
                    <p class="labs-example-item-name">一起交友</p>
                  </li>
                  <li class="labs-example-item">
                    <img class="imgwrap-pic" src="https://wuji-30130.sz.gfp.tencent-cloud.com/pics/20200318_7wbr2yla49.png" alt="">
                    <p class="labs-example-item-name">一起交友</p>
                  </li>
                  <li class="labs-example-item">
                    <img class="imgwrap-pic" src="https://wuji-30130.sz.gfp.tencent-cloud.com/pics/20200318_7wbr2yla49.png" alt="">
                    <p class="labs-example-item-name">一起交友</p>
                  </li>
                </ul>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <!-- 趣味课程名师名家带你学 -->
    <div class="page-home-inner" id="teach">
      <div class="page-home-panel-hd">
        <h2 class="page-home-panel-title">趣味课程，名师名家带你学</h2>
        <p class="page-home-panel-title-info">学习丰富的权威认证课程</p>
      </div>
      <div class="page-home-panel-bd">
        <div class="page-home-tabs">
          <div class="eui-tabs-nav filter-tabs">
            <div class="eui-tabs-nav-wrap">
              <div @click="gradeClick(item.id)" class="eui-tabs-tab" :class="state.gradeSelect === item.id ? 'current' : ''" v-for="item in state.gradeList" :key="item">
                <div class="eui-tabs-tab-link"><span class="eui-tabs-tab-label">{{item.grade}}</span></div>
              </div>
            </div>
          </div>
        </div>
        <div class="card-list course">
          <ul class="card-list-wrap">
            <li class="card-list-item" v-for="item in state.gradeList[state.gradeSelect].content" :key="item">
              <div class="img-w">
                <a href="">
                  <img class="card-cover-pic imgwrap-pic"
                    :src="item.img" alt="">
                  <span class="tag-w">简单</span>
                </a>
              </div>
              <p class="title-w">{{ item.text }}</p>
            </li>
          </ul>
        </div>
      </div>
    </div>
    <!-- 网页底部 -->
    <Footer></Footer>
    <!-- 右侧指引 -->
    <div class="sidebar" id="top"  :style="state.scrollTop > 500 ? 'position: filex;bottom: 80px;' : 'position: filex;bottom: -460px;'">
      <i class="icon-spr icon-spr-guide"></i>
      <ul class="sidebar-anchor-list" :style="state.scrollTop > 500 ? '' : 'display: none;'">
          <li @mouseenter="enter(item)" @mouseleave="leave()" :style="state.hoverCheck === item ? state.sidebarStyle : ''" class="sidebar-anchor-item" v-for="item in state.sidebarList" :key="item" @click="sidebarClick(item)">
              <img :src="img2" alt="">
              <span :style="state.selectCheck === item ? state.selectStyle : ''"  class="sidebar-anchor-item-text">{{ item }}</span>
        </li>
      </ul>
    </div>
  </div>
</template>

<script setup>
import { ElMessage } from 'element-plus';
import { reactive, onMounted, onUnmounted, ref } from 'vue';
import Footer from '../components/footer.vue';
import Head from '../components/head.vue';
import Wrapper from '../components/wrapper.vue';
const img1 = require('../assets/ico1.png');
const img2 = require('../assets/ico2.png');

const carouselSwich = ref(null);
const gradeClick = (id) => {
  state.gradeSelect = id;
}
onMounted(() => {
  window.addEventListener('scroll', hadnleScolly)
})

onUnmounted(() => {
  //清除监听器
  window.removeEventListener('scroll')
})

const labsClick = (id) => {
  state.toolSelect = id;
}

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

const hadnleScolly = () => {
  state.scrollTop = document.documentElement.scrollTop
}

const enter = (item) => {
  state.hoverCheck = item;
  state.sidebarStyle.background = '#009cff';
  state.sidebarStyle.color = '#fff';
}
const leave = () => {
  state.sidebarStyle.background = '#fff';
  state.sidebarStyle.color = '#ccc';
}
//指引点击
const sidebarClick = (item) => {
  state.selectCheck = item;
  state.selectImg = img2;
  state.sidebarStyle.background = '#fff';
  state.selectStyle.background = '#fff';
  state.selectStyle.color = '#009cff';
  let id = '';
  switch (state.selectCheck) {
    case '实验课':
      id = 'tool'
      break;
    case '学好课':
      id = 'teach'
      break;
    case '回到顶部':
      id = 'head'
  }
  jumpPosition(id)
}

const jumpPosition = (id) => {
  const positionTop = document.getElementById(id).offsetTop;
  console.log(positionTop,'positionTop');
  const scrolly = setInterval(() => {
    if (state.scrollTop - positionTop < 80 && state.scrollTop - positionTop> 0) {
       clearInterval(scrolly)
    }

    if (state.scrollTop - positionTop > 20) {
        document.documentElement.scrollTop -= 50;
    } else if (state.scrollTop - positionTop < 20) {
        document.documentElement.scrollTop += 20;
    } 
  }, 20)
}

const state = reactive({
  toolList: [
    {
      id: 0,
      title: '创意实验室',
      describe: ['6+岁', '创造力', '图形化'],
      ico: 'https://wuji-30130.sz.gfp.tencent-cloud.com/pics/20200306_g9ofq50ftsdcreative.png',
      content: {
        title: '像搭积木一样编程创作',
        text: '创意实验室',
        bdText: '让学编程和搭积木一样简单，有效帮助孩子形成编程思维，锻炼逻辑思维，轻松制作有趣有料的编程项目，发挥自己的无限创意。',
        video: 'https://wuji-30130.sz.gfp.tencent-cloud.com/20200317_qrjirl2blsbpython.mp4'
      }
    },
    {
      id: 1,
      title: 'Python实验室',
      describe: ['7', '岁逻辑思维', 'Python'],
      ico: 'https://wuji-30130.sz.gfp.tencent-cloud.com/pics/20200306_7h0exzofi7tpython.png',
      content: {
        title: '像搭积木一样编程创作',
        text: 'Python实验室',
        bdText: '让学编程和搭积木一样简单，有效帮助孩子形成编程思维，锻炼逻辑思维，轻松制作有趣有料的编程项目，发挥自己的无限创意。',
        video: 'https://wuji-30130.sz.gfp.tencent-cloud.com/20210516_rfqbytd62t.MP4'
      }
    },
    {
      id: 2,
      title: '腾讯口顶-编程第一课',
      describe: ['6-9岁', '编程启蒙', '计算思维'],
      content: {
        title: '腾讯口顶-编程第一课',
        text: '创意实验室',
        bdText: '让学编程和搭积木一样简单，有效帮助孩子形成编程思维，锻炼逻辑思维，轻松制作有趣有料的编程项目，发挥自己的无限创意。',
        video: 'https://wuji-30130.sz.gfp.tencent-cloud.com/20200317_ojl6d4y4ciq.mp4'
      },
      ico: 'data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABoAAAAiCAYAAABBY8kOAAAEFElEQVRIia2XX0wcVRTGf3NnlyW0S11boLS1FhpLADXWKqCl0QbTmFRTNT5oYoyvuIkaEx/wyRfdN01MiL41vhijSY1SH7Q2TYWaUPoHWwoNVFppkQCtlUJhd2dmx9zZuduZ2eXf4vcyOefc+31z7px77h1tsu09lkEV8DLQCuwFtgApYBw4C/QA3wOTS9E4QtFEPC8w29HZBHwONC/3Ji56gXeiifjpAI/zFIVmzHZ0drgTVyqCO7bXnZuHUEDgEeALd4my0AWh+hpCjbXoD1YjysuwzQz2nTms8WnMS6OYQ1fByqgZn8x2dB4E2qOJ+EXlDAWUfSKh+h1EDrYiNm7wDdJ0Ha0ihqiIEX5sF5lbM6R+6sEcuqaG7HW5WnPv+0FtC5HnmmQ2HwJvZZkgcqCF0kPPoJWVLrtmckz40V1oIR1r9IZyb08f7zOBblQxAE8Dp9SIyIFmSvY/saxAIaRPnCH1S683IrP7XRXDp/eWq4aSZ4sTkZBzQw01XpfDLdx9ka0uXRB5cZ+zdEVDLvsL+xwuF5J7a8jdjNlsGmsRsWhOIjNxk+SRE2SmbiMqY5S+sh9RvWnZuOQINe7EvDCihr4kvJURbqj15bHw7a9YN6aw04bzlPZK42H/8rVKoSZliQeqfESZqX+KtsV2H1ez+kbZYPk6H7HcJ8XaIurj2iKFclvatm0fcemrbYjNG0HXnbWX9orjmq+iRMjtwg85QjNzaJvuy0X1bZWse/c1FsNScXtu3mtOyowuKysz/e+ipKuF9fdN74zzwj1PHJiXr62VP4cAV48UOpoL9g9jzyfXLCI5JJcHR6XQINDvDEgbwT5VFFLHeh0uF5J7UPWJ3GFlnB5wzphiYY5cx+gd8M52uJXQTM6taQhP5a0WemUMhO6ddckrlOve4d11iKr7ixbSNqwn/LCvlb2hhCqAFsclBCVtTxYtohDaXec1DymhN3MD6ncgYuVrF9q5LXhMhP3d+/G6RSevTklHW1/m9WyWQnuUpW+t/H+ELAv77oLXM13wXrcWAQmjbwhMS3nPAEl/Cxoec5723STmwJ+r1jH6R5j7+DDJH0963Z/h3ut+Bl6XRqqr29lw1pXraKUR52gPtHuM/mGs0XEizz+VdxWzRsaCXVverL7GrbqvgHNOJoaJefEK9kKKzO07GH+M4GfKkPrhJEbfIOnu876QPGKMwatBkXZlqG/UrsS8cDIcHssK35oh2dWNnUxnMzt1AeuvCcjYThYL3xwDw1Szz0YT8da8K7H7B7BntqOz2i33j4AG2YUXDncV/B4y+/kvjxSMAe8HHb6qiybiE9FE/Ds3w9zdtgDu9cZ8vB1NxH8Lupf6EZMNTwrKDOXuvuVWqLy8y58uFZPtSx6nKnY8jwn4DzeQgHU7MSGyAAAAAElFTkSuQmCC'
    },
    {
      id: 3,
      title: '3D实验室',
      describe: ['6岁', '创造力', '3D立体'],
      ico: 'https://wuji-30130.sz.gfp.tencent-cloud.com/pics/20200429_ir7137irhcn48X48.png',
      content: {
        title: '像搭积木一样编程创作',
        text: '创意实验室',
        bdText: '让学编程和搭积木一样简单，有效帮助孩子形成编程思维，锻炼逻辑思维，轻松制作有趣有料的编程项目，发挥自己的无限创意。',
        video: 'https://wuji-30130.sz.gfp.tencent-cloud.com/20200430_qdivvm8bin.mp4'
      }
    },
    {
      id: 4,
      title: '人工智能实验室',
      describe: ['10+岁', '前沿科技', '走进AI'],
      ico: 'https://wuji-30130.sz.gfp.tencent-cloud.com/20200430_nhuts1fwacd.mp4',
      content: {
        title: '人工智能实验室',
        text: '创意实验室',
        bdText: '让学编程和搭积木一样简单，有效帮助孩子形成编程思维，锻炼逻辑思维，轻松制作有趣有料的编程项目，发挥自己的无限创意。',
        video: 'https://wuji-30130.sz.gfp.tencent-cloud.com/20200317_qrjirl2blsbpython.mp4'
      }
    },
    {
      id: 5,
      title: '游戏实验室',
      describe: ['6-8岁', '创意游戏', '零基础'],
      ico: 'https://wuji-30130.sz.gfp.tencent-cloud.com/pics/20200306_16yws3wyo7hgame.png',
      content: {
        title: '游戏实验室',
        text: '创意实验室',
        bdText: '让学编程和搭积木一样简单，有效帮助孩子形成编程思维，锻炼逻辑思维，轻松制作有趣有料的编程项目，发挥自己的无限创意。',
        video: 'https://wuji-30130.sz.gfp.tencent-cloud.com/20200317_qrjirl2blsbpython.mp4'
      }
    },
    {
      id: 6,
      title: '艺术(P5)实验室',
      describe: ['7+sui', '艺术表达', '数理知识'],
      ico: 'https://wuji-30130.sz.gfp.tencent-cloud.com/pics/20200306_otye6yv5nvart.png',
      content: {
        title: '艺术(P5)实验室',
        text: '创意实验室',
        bdText: '让学编程和搭积木一样简单，有效帮助孩子形成编程思维，锻炼逻辑思维，轻松制作有趣有料的编程项目，发挥自己的无限创意。',
        video: 'https://wuji-30130.sz.gfp.tencent-cloud.com/20200430_k5b1bg002nl.mp4'
      }
    },
  ],
  toolSelect: 0,
  sidebarList: ['实验课','学好课','好作品','咨询','校园','合作','回到顶部'],
  hoverCheck: '',
  selectCheck: '实验课',
  sidebarStyle: {

  },
  selectStyle: {

  },
  selectImg: img1,
  carouselIndex: 0,
  scrollTop: 0,
  gradeList: [
    {
      id: 0,
      grade: '编辑推荐',
      content: [
        {
          text: '白细胞大作战',
          img: 'https://wuji-30130.sz.gfp.tencent-cloud.com/pics/20200318_c22d8kc2e5f.png'
        },
        {
          text: '消防车出击',
          img: 'https://wuji-30130.sz.gfp.tencent-cloud.com/pics/20200318_vz2jmyadnh.png'
        },
        {
          text: '贪吃鸡',
          img: 'https://p.qpic.cn/qqgameedu/0/3d331987fa9216a04cf5435ab3d2b07c/0'
        },
        {
          text: '贪吃鸡',
          img: 'https://p.qpic.cn/qqgameedu/0/3d331987fa9216a04cf5435ab3d2b07c/0'
        },
        {
          text: '贪吃鸡',
          img: 'https://p.qpic.cn/qqgameedu/0/3d331987fa9216a04cf5435ab3d2b07c/0'
        },
        {
          text: '贪吃鸡',
          img: 'https://p.qpic.cn/qqgameedu/0/3d331987fa9216a04cf5435ab3d2b07c/0'
        },
        {
          text: '科普八大行星',
          img: 'https://p.qpic.cn/qqgameedu/0/3d331987fa9216a04cf5435ab3d2b07c/0'
        },
        {
          text: '科普八大行星',
          img: 'https://p.qpic.cn/qqgameedu/0/3d331987fa9216a04cf5435ab3d2b07c/0'
        },
      ]
    },
    {
      id: 1,
      grade: '低年级（三年级或以下）',
      content: [
        {
          text: '贪吃鸡',
          img: 'https://p.qpic.cn/qqgameedu/0/3d331987fa9216a04cf5435ab3d2b07c/0'
        },
        {
          text: '科普八大行星',
          img: 'https://p.qpic.cn/qqgameedu/0/3d331987fa9216a04cf5435ab3d2b07c/0'
        },
        {
          text: '趣味打气球',
          img: 'https://p.qpic.cn/qqgameedu/0/3d331987fa9216a04cf5435ab3d2b07c/0'
        },
        {
          text: 'JS实验室绘图',
          img: 'https://wuji-30130.sz.gfp.tencent-cloud.com/pics/20200318_rf46gppvaaf.png'
        },
        {
          text: '科普八大行星',
          img: 'https://p.qpic.cn/qqgameedu/0/3d331987fa9216a04cf5435ab3d2b07c/0'
        },
        {
          text: '趣味打气球',
          img: 'https://p.qpic.cn/qqgameedu/0/3d331987fa9216a04cf5435ab3d2b07c/0'
        },
        {
          text: '科普八大行星',
          img: 'https://p.qpic.cn/qqgameedu/0/3d331987fa9216a04cf5435ab3d2b07c/0'
        },
        {
          text: '趣味打气球',
          img: 'https://p.qpic.cn/qqgameedu/0/3d331987fa9216a04cf5435ab3d2b07c/0'
        },
      ]
    },
    {
      id: 2,
      grade: '高年级（四年级或以上）',
      content: [
        {
          text: '贪吃鸡',
          img: 'https://p.qpic.cn/qqgameedu/0/3d331987fa9216a04cf5435ab3d2b07c/0'
        },
        {
          text: '科普八大行星',
          img: 'https://p.qpic.cn/qqgameedu/0/3d331987fa9216a04cf5435ab3d2b07c/0'
        },
        {
          text: '趣味打气球',
          img: 'https://p.qpic.cn/qqgameedu/0/3d331987fa9216a04cf5435ab3d2b07c/0'
        },
        {
          text: 'JS实验室绘图',
          img: 'https://wuji-30130.sz.gfp.tencent-cloud.com/pics/20200318_rf46gppvaaf.png'
        },
        {
          text: '科普八大行星',
          img: 'https://p.qpic.cn/qqgameedu/0/3d331987fa9216a04cf5435ab3d2b07c/0'
        },
        {
          text: '趣味打气球',
          img: 'https://p.qpic.cn/qqgameedu/0/3d331987fa9216a04cf5435ab3d2b07c/0'
        },
        {
          text: '科普八大行星',
          img: 'https://p.qpic.cn/qqgameedu/0/3d331987fa9216a04cf5435ab3d2b07c/0'
        },
        {
          text: '趣味打气球',
          img: 'https://p.qpic.cn/qqgameedu/0/3d331987fa9216a04cf5435ab3d2b07c/0'
        },
      ]
    },
    {
      id: 3,
      grade: '初中及以上',
      content: [
        {
          text: 'JS实验室绘图',
          img: 'https://wuji-30130.sz.gfp.tencent-cloud.com/pics/20200318_rf46gppvaaf.png'
        },
        {
          text: '科普八大行星',
          img: 'https://p.qpic.cn/qqgameedu/0/3d331987fa9216a04cf5435ab3d2b07c/0'
        },
        {
          text: '科普八大行星',
          img: 'https://p.qpic.cn/qqgameedu/0/3d331987fa9216a04cf5435ab3d2b07c/0'
        },
        {
          text: '贪吃鸡',
          img: 'https://p.qpic.cn/qqgameedu/0/3d331987fa9216a04cf5435ab3d2b07c/0'
        },
        {
          text: '科普八大行星',
          img: 'https://p.qpic.cn/qqgameedu/0/3d331987fa9216a04cf5435ab3d2b07c/0'
        },
        {
          text: '趣味打气球',
          img: 'https://p.qpic.cn/qqgameedu/0/3d331987fa9216a04cf5435ab3d2b07c/0'
        },
        {
          text: 'JS实验室绘图',
          img: 'https://wuji-30130.sz.gfp.tencent-cloud.com/pics/20200318_rf46gppvaaf.png'
        },
        {
          text: '科普八大行星',
          img: 'https://p.qpic.cn/qqgameedu/0/3d331987fa9216a04cf5435ab3d2b07c/0'
        },
      ]
    },
  ],
  gradeSelect: 0
})

const handleCommand = (command) => {
  ElMessage(`click on item ${command}`)
}
</script>

<style lang='less'>
.page-home {
  background: #eff3f8;
}
.labs-nav-item.current::before {
    display: block;
}

.labs-nav-item::before {
    content: '';
    width: 4px;
    position: absolute;
    left: 0;
    top: 0;
    height: 82px;
    background: #0080ff;
    display: none;
}
.current {
  background: #fff;
}

ul.el-carousel__indicators.el-carousel__indicators--horizontal.el-carousel__indicators--outside {
  display: none;
}

.page-home-panel-hd {
  padding-bottom: 26px;
}


.slide-imgwrap-pic {
  display: block;
  max-width: 100%;
  margin: 0 auto;
  object-fit: cover;
  object-position: 50% 50%;
}

.slide-nav-btn.prev .iconhome {
    display: inline-block;
    transform: rotate(180deg);
}

.labs-nav-item {
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
  height: 82px;
  position: relative;
  cursor: pointer;
  padding: 0 20px;
  border-bottom: 1px solid #0090ff;
  .labs-nav-item-icon {
    width: 48px;
    height: 48px;
    background: #fff;
    border-radius: 12px;
    text-align: center;
    margin-right: 14px;
    transition: all 200ms;
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
  }

  .labs-nav-item-icon-pic {
    display: block;
    margin: 0 auto;
    transition: all 200ms;
  }

  .labs-nav-item-title {
    font-size: 18px;
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
    width: 180px;
    text-align: left;
  }

  .labs-nav-item-info {
    font-size: 12px;
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
    width: 180px;
    text-align: left;
  }
}

  .labs-nav-item:hover {
    .labs-nav-item-icon {
      background-color: rgb(251, 232, 194);
      border-radius: 30px;
    }
    // background: #0090ff;
  }

  .labs-intro-cover .video-player-wrapper {
      width: 360px;
      height: 270px;
      margin-left: 40px;
  }

.sidebar {
  width: 110px;
  position: fixed;
  bottom: 80px;
  right: 1%;
  z-index: 13;
  height: 705px;
  transition: all 200ms;
}

.sidebar-anchor-list {
  width: 60px;
  margin: 0 auto;
  background: #fff;
  border-radius: 8px;
  box-shadow: 0px 0px 4px rgba(74, 89, 111, 0.2);
}

.icon-spr-guide {
    background-position: 0px -279px;
    width: 102px;
    height: 136px;
}

.icon-spr {
    display: inline-block;
    background-image: url('../assets/right.png');
}

.sidebar-anchor-item {
    height: 68px;
    border-bottom: 1px solid #eff3f8;
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
    -webkit-box-pack: center;
    -webkit-justify-content: center;
    -ms-flex-pack: center;
    justify-content: center;
    text-align: center;
    font-size: 12px;
    transition: all 200ms;
    flex-direction: column;
    cursor: pointer;
    img {
      width: 20px;
      height: 18px;
      margin-bottom: 6px;
    }
}

.sidebaricon-course:before {
    content: "\e646";
}

  .labs-example-list {
    width: 850px;
    margin-top: 8px;
    .labs-example-item {
        float: left;
        width: 258px;
        height: 200px;
        margin-right: 18px;
        .imgwrap-pic {
            transform: scale(1) translateZ(0);
            transition: all 220ms;
            overflow: hidden;
            cursor: pointer;
            border-radius: 4px;
        }
        .imgwrap-pic:hover {
          transform: scale(1.02);
        }
        .labs-example-item-name {
            margin-top: 8px;
            overflow: hidden;
            text-overflow: ellipsis;
            display: -webkit-box;
            -webkit-box-orient: vertical;
            -webkit-line-clamp: 2;
        }
    }
  }

  .labs-example-hd {
    display: flex;
    justify-content: space-between;
  }

.el-carousel__item h3 {
  display: flex;
  color: #475669;
  opacity: 0.75;
  line-height: 300px;
  margin: 0;
}

.page-home-panel-title {
  font-size: 40px;
  font-weight: bold;
}

.page-home-panel-title-info {
  font-size: 16px;
  color: rgba(74, 89, 111, 0.6);
}

.page-home-inner {
  padding-top: 80px;
  width: 1200px;
  margin: 0 auto;
}

.page-home-panel-bd {
  .labs {
    border-radius: 12px;
    background: #fff;
    height: 600px;
    overflow: hidden;
    display: -webkit-box;
    display: -webkit-flex;
    display: -ms-flexbox;
    display: flex;
    -webkit-box-orient: horizontal;
    -webkit-box-direction: normal;
    -webkit-flex-flow: row wrap;
    -ms-flex-flow: row wrap;
    flex-flow: row wrap;

    .labs-aside {
      width: 290px;
      background: #009cff;
    }

    .labs-main {
      width: 810px;
      margin-left: 50px;
      text-align: left;
      .labs-intro {
          padding-top: 30px;
          display: -webkit-box;
          display: -webkit-flex;
          display: -ms-flexbox;
          display: flex;
          -webkit-box-orient: horizontal;
          -webkit-box-direction: normal;
          -webkit-flex-flow: row wrap;
          -ms-flex-flow: row wrap;
          flex-flow: row wrap;
          width: 812px;
          border-bottom: 1px solid rgba(74, 89, 111, 0.1);
          padding-bottom: 20px;
          margin-bottom: 20px;
          .labs-intro-figure {
            width: 410px;
          }
      }
      .labs-intro-figure-title {
          font-size: 24px;
          margin: 23px 0 12px;
      }
      .labs-intro-figure-description {
        color: rgba(74, 89, 111, 0.6);
        line-height: 30px;
        overflow: hidden;
        text-overflow: ellipsis;
        display: -webkit-box;
        -webkit-box-orient: vertical;
        -webkit-line-clamp: 3;
        height: 90px;
    }
    }
  }
}

.page-home-tabs {
  height: 34px;
  margin-bottom: 16px;
}

.filter-tabs {
  flex: 1;
  border-bottom: none;
}

.filter-tabs .eui-tabs-nav-wrap {
  height: 34px;
  top: 0;
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
  justify-content: center;
}

.filter-tabs .eui-tabs-tab.current {
  background: #009cff;
}

.filter-tabs .eui-tabs-tab {
  margin: 0 10px;
  min-width: 110px;
  height: 34px;
  line-height: 34px;
  background: #f0f3f7;
  border-radius: 17px;
  text-align: center;
  cursor: pointer;
}

.eui-tabs-tab.current {
  background-color: #4a596f;
  border-radius: 2px 2px 0 0;
  border-radius: 17px;
}

.eui-tabs-tab {
  float: left;
  margin-right: 3px;
}

.card-list.course {
  padding-top: 24px;

  .card-list-wrap {
    .card-list-item {
      // float: left;
      width: 288px;
      height: 386px;
      margin: 0 16px 15px 0;
    }
  }
}

.el-carousel__item:nth-child(2n) {
  background-color: #99a9bf;
}

.el-carousel__item:nth-child(2n + 1) {
  background-color: #d3dce6;
}

.card-list-wrap {
  display: flex;
  flex-wrap: wrap-reverse;

  .card-list-item {
    overflow: hidden;

    width: 288px;
    height: 290px !important;
    box-sizing: border-box;
    // background-color: red;

    .img-w {
      overflow: hidden;
      width: 288px;
      height: 226px;

      .card-cover-pic:hover {
        transform: scale(1.03);
        transition: all 0.3s;
      }
    }
    .title-w{
      text-align: left;
      font-size: 16px;
      color: #4a596f;
      margin-top: 12px;
    }


  }

  .card-list-item:nth-child(4),
  .card-list-item:nth-child(8) {
    margin-right: 0 !important;
  }

  .tag-w {
    display: inline-block;
    position: relative;
    top: -220px;
    left: -100px;
    background: #00ce9e;
    line-height: 22px;
    text-align: center;
    color: #fff;
    font-size: 14px;
    box-shadow: 0 2px 5px rgb(0 0 0 / 10%);
    border-radius: 2px 11px 11px 2px;
    z-index: 3;
    width: 50px;
    height: 22px;
  }
}
</style>
