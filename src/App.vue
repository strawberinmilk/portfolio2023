<template>
  <el-page-header :id="$style.header" :icon="null">
    <template #title>
      <router-link to="/">
        <span>rin;</span>
      </router-link>
    </template>
    <template #icon>
      <div :id="$style.headerHeight"></div>
    </template>
    <template #content>
      <a href="/#about">about</a>
      <a href="/#komichi">小路綾bot</a>
      <a href="/#qualification">資格</a>
      <a href="/#links">リンク</a>
    </template>
  </el-page-header>
  <div :id="$style.headerHeightKeep"></div>
  <div id="progressAppGsap" :class="$style.progress"></div>
  <router-view />
</template>

<script>
import { defineComponent } from 'vue';
import { gsap } from 'gsap';
import { ScrollTrigger } from 'gsap/ScrollTrigger';

gsap.registerPlugin(ScrollTrigger);
export default defineComponent({
  name: 'App',
  mounted() {
    gsap.set('#progressAppGsap', {
      width: '0%',
    });
    gsap.to('#progressAppGsap', {
      width: '100%',
      scrollTrigger: {
        start: 'top top',
        end: 'bottom center',
        toggleActions: 'play reverse play reverse',
        scrub: true,
        //markers: true,
      },
    });
  },
});
</script>

<style lang="scss" module>
@use '@/constants/constants.scss';
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin: 0;
}

#header {
  color: #ffffff;
  background-color: #89a0f8;
  position: fixed;
  width: 100%;
  top: 0px;
  z-index: 1023;
  #headerHeight {
    height: constants.$HEADER_HEIGHT;
    width: 0px;
    /*headerは一番heightの大きいもののサイズで上下中央寄せされるよ*/
  }
  a {
    padding-left: 10px;
  }
}
#headerHeightKeep {
  height: constants.$HEADER_HEIGHT;
}

.progress {
  position: fixed;
  top: constants.$HEADER_HEIGHT;
  height: 10px;
  background-color: #c7fad5;
}
</style>
