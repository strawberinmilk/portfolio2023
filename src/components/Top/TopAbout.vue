<template>
  <div :id="$style.parent">
    <div :id="$style.inner">
      <h3>info</h3>
      <p>エンジニア。IT会社の役員してる。</p>
      <p>フロンドからゴリゴリのWebシステム、IoTの電子工作までなんでもやる。</p>
      <p>JavaScript / Node.js / TypeScript / Vue.js / Express</p>
      <p>ESP32/RaspberryPi</p>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'TopAbout',
});
</script>

<style lang="scss" module>
@use '@/constants/constants.scss';
#parent {
  height: calc(100% - constants.$HEADER_HEIGHT - constants.$PROGRESS_HEIGHT);
  width: 100%;
  text-align: center;
}
#inner {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translateY(-50%) translateX(-50%);
  width: 70%;
  background-color: #dbfec8;
  border: dashed 2px #ffffff;
  border-left: 5px solid #ffa9ff;
  border-radius: 10px;
  box-shadow: 0 2px 6px rgba(0, 0, 0, 0.3);
}
</style>
