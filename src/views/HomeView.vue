<template>
  <div id="parent">
    <TopPage />
    <TopAbout class="animation" msg="1" />
    <div class="trigger"></div>
    <TopKomichi class="animation" msg="2" />
    <div class="trigger"></div>
    <Product class="animation" msg="2" />
    <div class="trigger"></div>
    <TopQualification class="animation" msg="4" />
    <div class="trigger"></div>
    <TopLinks class="animation" msg="3" />
    <div class="trigger"></div>
  </div>
  <div style="height: 500px"></div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import TopPage from '@/components/Top/TopPage.vue';
import TopAbout from '@/components/Top/TopAbout.vue';
import Product from '@/components/Top/TopProduct.vue';
import TopKomichi from '@/components/Top/TopKomichi.vue';
import TopQualification from '@/components/Top/TopQualification.vue';
import TopLinks from '@/components/Top/TopLinks.vue';
import { gsap } from 'gsap';
import { ScrollTrigger } from 'gsap/ScrollTrigger';
gsap.registerPlugin(ScrollTrigger);

export default defineComponent({
  name: 'HomeView',
  components: {
    TopPage,
    TopAbout,
    Product,
    TopKomichi,
    TopLinks,
    TopQualification,
  },
  mounted() {
    const triggers: any[] = gsap.utils.toArray('.trigger'); // eslint-disable-line
    const animations: any[] = gsap.utils.toArray('.animation'); // eslint-disable-line
    for (const i in triggers) {
      gsap.set(animations[i], {
        x: window.outerWidth * (Number(i) % 2 ? 1 : -1) * 1.5,
        y: 0,
        opacity: 1,
        rotate: -90,
      });
      gsap.to(animations[i], {
        x: 0,
        y: 0,
        opacity: 1,
        rotation: 0,
        duration: 1,
        scrollTrigger: {
          trigger: triggers[i],
          start: 'top center',
          end: 'bottom center',
          toggleActions: 'play reverse play reverse',
          // scrub: true,
          markers: true,
        },
      });
    }
  },
});
</script>

<style lang="scss">
@use '@/constants/constants.scss';
body {
  background-color: #edc8d1;
}
.animation {
  position: fixed;
  top: calc(constants.$HEADER_HEIGHT + constants.$PROGRESS_HEIGHT);
  left: 0;
  margin: 0;
}
.trigger {
  margin: 0;
  height: 500px;
}
</style>
