<script setup lang="ts">
import { ref, onMounted } from "vue";
import { useDark } from "@vueuse/core"; // 引入暗黑模式
import Axios from "axios";

const isDark = ref(useDark());
// const news = ref();
// Axios.get("/api")
//   .then((res) => {
//     console.log(res);
//     if (res.status == 200) {
//       news.value = res.data.data.news;
//     }
//   })
//   .catch((err) => {
//     console.log(err);
//   });

// 定义静态的新闻数据
const news = ref([
  {
    title: "Here AIxOmics comes!",
    introduction: "",
    link: "https:aixomics.biometa.top",
    datetime: "2023-09-18",
    address: "AIxOmics is an open-source community dedicated to the deep integration of artificial intelligence (AI) and life sciences, dedicated to promoting innovative applications of AI technology in the field of life sciences. The community is centered around AI office tools, AI big models, and AI agents, focusing on cutting-edge AI technologies and the latest developments, providing members with an efficient platform for content exchange and learning. Through open collaboration, AIxOmics helps researchers quickly master AI technology, improve research efficiency and work capabilities, and contribute to breakthroughs and development in the field of life sciences.",
    isShow: true
  }
]);

const screenWidth = ref();
screenWidth.value = document.body.clientWidth;
// console.log("111111111", screenWidth);
window.onresize = () => {
  screenWidth.value = document.body.clientWidth;
  // console.log("222222222", screenWidth);
};

// onMounted(() => {
// })
</script>

<template>
  <!-- 首页背景图 -->
  <div class="home-background"></div>
  <!-- 首页导语 -->
  <el-row class="home-intro">
    <el-col :span="2"></el-col>
    <el-col :span="20">
      <h1>Welcome!</h1>
      <h2>AIxOmics Open Source Community</h2>
      <span>AIxOmics is an open-source community dedicated to the deep integration of artificial intelligence (AI) and life sciences, dedicated to promoting innovative applications of AI technology in the field of life sciences.</span>
    </el-col>
    <el-col :span="2"></el-col>
  </el-row>
  <!-- 首页内容 -->
  <div>
    <el-row :style="{ 'background-color': !isDark ? '#cdd1d3' : '#131124' }">
      <el-col :span="2"></el-col>
      <el-col :span="20">
        <!-- 招兵买马 -->
        <div class="home-recruiting">
          <el-row>
            <!-- 8→24 -->
            <!-- <el-col :span="8"> -->
            <el-col :span="screenWidth > 1200 ? 8 : 24">
              <h1>Hot News</h1>
            </el-col>
            <!-- 14→24，2→0 -->
            <!-- <el-col :span="14" :offset="2"> -->
            <el-col :span="screenWidth > 1200 ? 14 : 24" :offset="screenWidth > 1200 ? 2 : 0">
              <div v-for="(n, index) in news" :key="index">
                <!-- <h2>This is an Advertisement space</h2> -->
                <h2>
                  {{ n.title }}
                  <el-link target="_blank" type="primary" :href="n.link" style="font-size: 16px; font-weight: bold">
                    Link
                  </el-link>
                </h2>
                <h4>{{ n.datetime }}</h4>
                <h4>{{ n.address }}</h4>
                <p class="web-text">{{ n.introduction }}</p>
                <!-- 分割线 -->
                <el-divider style="margin-top: 100px"></el-divider>
              </div>
            </el-col>
          </el-row>
        </div>
      </el-col>
      <el-col :span="2"></el-col>
    </el-row>
  </div>
</template>

<style scoped>
.home-background {
  width: 100%;
  min-height: 100%;
  background: url("./../assets/home-test.png") center center no-repeat;
  background-size: 100% 100%;
  position: fixed;
  z-index: -1;
  overflow: auto;
}

.home-intro {
  padding: 100px 0 220px 0;
  color: white;
  /* border: 1px solid green; */
}

.home-intro h1 {
  font-size: 80px;
}

.home-intro h2 {
  font-size: 60px;
}

.home-intro span {
  font-size: 48px;
  line-height: 1.2;
}

.home-recruiting {
  padding: 50px 0 80px 0;
}

/* 判断屏幕宽度小于1080px后使用百分比 */
@media screen and (max-width: 1200px) {
  .home-intro {
    padding: 100px 0 200px 0;
  }

  .home-intro h1 {
    font-size: 64px;
  }

  .home-intro h2 {
    font-size: 46px;
  }

  .home-intro span {
    font-size: 32px;
  }
}

/* 判断屏幕宽度小于640px后使用百分比 */
@media screen and (max-width: 640px) {
  .home-intro {
    padding: 100px 0 180px 0;
  }

  .home-intro h1 {
    font-size: 52px;
  }

  .home-intro h2 {
    font-size: 36px;
  }

  .home-intro span {
    font-size: 28px;
  }
}
</style>
