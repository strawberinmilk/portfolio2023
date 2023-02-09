<template>
  <div id="parent">
    <TopPage />
    <TopAbout class="animation" msg="1" />
    <div id="about" class="trigger"></div>
    <TopKomichi class="animation" msg="2" />
    <div id="komichi" class="trigger"></div>
    <TopQualification class="animation" msg="4" />
    <div id="qualification" class="trigger"></div>
    <TopLinks class="animation" msg="3" />
    <div id="links" class="trigger"></div>
  </div>
  <div id="footer">
    <p>閲覧ありがとうございました。</p>
    <img id="footerPic" src="@/assets/footer_pic.jpg" />
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import TopPage from '@/components/Top/TopPage.vue';
import TopAbout from '@/components/Top/TopAbout.vue';
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
          // markers: true,
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
  z-index: 500;
}
.trigger {
  margin: 0;
  height: 500px;
}
#footer {
  height: 500px;
  text-align: center;
}
#footerPic {
  position: relative;
  width: 100%;
  height: 200px;
  margin-top: 300px;
  object-fit: cover;
  mask-image: linear-gradient(transparent, black);
}
</style>
