/*
 * @Author: web.zlz
 * @Date: 2024-06-14 15:50:42
 * @LastEditors: longze
 * @LastEditTime: 2024-06-14 15:50:42
 * @Description: file content
*/
<template>
  <!-- <div style="height:150px; margin-top:100px">
    <d-slider v-model="options.volume"></d-slider>
  </div>-->
  <div style="text-align: center">
    {{ options.webFullScreen }}
    <button
      @click="change"
    >
      {{ options.src }}
    </button>
    <longzeVideoPlay
      ref="videoRef"
      style="display: inline-block; width: 100%"
      v-bind="options"
    />
  </div>
  <button @click="test">test</button>
</template>

<script setup lang="ts">
import { reactive, ref, nextTick } from "vue";
import { longzeVideoPlay } from "../lib/index.js";

const options = reactive({
  width: "800px",
  height: "450px",
  color: "#409eff",
  muted: false, //静音
  webFullScreen: false,
  autoPlay: false, //自动播放
  currentTime: 0,
  loop: false, //循环播放
  mirror: false, //镜像画面
  ligthOff: false, //关灯模式
  volume: 0.3, //默认音量大小
  control: true, //是否显示控制器
  title: "", //视频名称
  type: "m3u8",
  src: "https://test-streams.mux.dev/x36xhzz/x36xhzz.m3u8", //视频源
  // src: "https://bitdash-a.akamaihd.net/content/sintel/hls/playlist.m3u8", //视频源
  // src: "https://logos-channel.scaleengine.net/logos-channel/live/biblescreen-ad-free/playlist.m3u8", //视频源
  // poster: "https://cdn.jsdelivr.net/gh/xdlumia/files/video-play/ironMan.jpg", //封面
  controlBtns: [
    "audioTrack",
    "quality",
    "speedRate",
    "volume",
    "setting",
    "pip",
    "pageFullScreen",
    "fullScreen",
  ],
});
const videoRef = ref(null);
const test = () => {
  console.log(videoRef.value);
  // video.value.test();
  videoRef.value.destroyHLS();
};
const change = () => {
  options.src = 'https://bitdash-a.akamaihd.net/content/sintel/hls/playlist.m3u8'
  options.type = "m3u8"
};
nextTick(() => {
  console.log(videoRef.value);
});
</script>

<style scoped>
</style>
