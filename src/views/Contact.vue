<script setup lang="ts">
import { ref, reactive, onMounted } from "vue";
import { useDark } from "@vueuse/core"; // 引入暗黑模式
// import mapHTML from "./../assets/api/Map.html";

const isDark = ref(useDark());
const contact = reactive({
  // map: "/api/Map.html",
  // map: mapHTML,
  map: ""
});

const screenWidth = ref();
screenWidth.value = document.body.clientWidth;
window.onresize = () => {
  screenWidth.value = document.body.clientWidth;
};
// onMounted(() => {
// })
</script>

<template>
  <!-- 简述 -->
  <div class="wrapper-background"></div>
  <div class="wrapper-sketch">
    <el-row>
      <el-col :span="2"></el-col>
      <el-col :span="20">
        <el-row>
          <el-col
            class="wrapper-sketch-text"
            :span="screenWidth > 1200 ? 14 : 24"
          >
            <div class="wrapper-sketch-text-title">Contact</div>
            <div class="wrapper-sketch-text-subtitle">
              Our Detail Information
            </div>
            <h1 class="wrapper-sketch-text-content">Contact us at any time</h1>
          </el-col>
        </el-row>
      </el-col>
      <el-col :span="2"></el-col>
    </el-row>
  </div>
  <!-- 内容 -->
  <!-- 首页内容 -->
  <el-row :style="{ 'background-color': !isDark ? '#cdd1d3' : '#131124' }">
    <el-col :span="2"></el-col>
    <el-col :span="20">
      <div class="contact-recruiting">
        <el-row>
          <!-- 8→24 -->
          <el-col :span="screenWidth > 1200 ? 8 : 24">
            <h1>Contact us</h1>
            <p class="web-text">Ze Zhang</p>
            <p class="web-text">
              BGI Hangzhou Research
            </p>
            <p class="web-text">
              No.202 Zhenzhong Road, Hangzhou 310030, Zhejiang Province, China
            </p>
            <p class="web-text">TEL : +86-19276868848</p>
            <p class="web-text">E-mail : zhangze1@genomics.cn</p>
          </el-col>
          <!-- 14→24，2→0 -->
          <el-col
            :span="screenWidth > 1200 ? 14 : 24"
            :offset="screenWidth > 1200 ? 2 : 0"
            v-if="contact.map"
          >
            <iframe
              :style="
                screenWidth > 1200
                  ? 'width: 100%; height: 100%;'
                  : 'width: 100%; height: 400px; margin-top: 30px;'
              "
              :src="contact.map"
              frameborder="0"
            ></iframe>
          </el-col>
        </el-row>
      </div>
    </el-col>
    <el-col :span="2"></el-col>
  </el-row>
</template>
<style scoped>
.contact-recruiting {
  padding: 50px 0 80px 0;
}
</style>
