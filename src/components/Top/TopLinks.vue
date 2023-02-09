<template>
  <div :id="$style.parent">
    <div :id="$style.inner">
      <h3>links</h3>
      <el-row>
        <el-col id="twitter" :span="0" :sm="12">
          Twitter
          <a
            class="twitter-timeline"
            data-height="500"
            data-theme="light"
            href="https://twitter.com/strawbeRinMilk?ref_src=twsrc%5Etfw"
            >Tweets by strawbeRinMilk</a
          >
        </el-col>
        <el-col :span="24" :sm="12">
          <a
            href="https://twitter.com/strawberinmilk?ref_src=twsrc%5Etfw"
            class="twitter-follow-button"
            data-show-count="false"
            >Follow @strawberinmilk</a
          >
          <p>
            <a href="https://github.com/strawberinmilk">
              <img :id="$style.githubImg" src="/github.png" />
            </a>
          </p>
          <p>
            <a href="https://qiita.com/strawbeRinMilk">Qiita</a>
          </p>
          <p>
            <a href="https://www.amazon.jp/hz/wishlist/ls/9A75OFYW2EJI?ref_=wl_share">Amazon</a>
          </p>
        </el-col>
      </el-row>
    </div>
  </div>
</template>
<script lang="ts">
import { defineComponent } from 'vue';
export default defineComponent({
  name: 'TopLinks',
  mounted() {
    setTimeout(() => {
      const tweetScript = document.createElement('script');
      tweetScript.setAttribute('src', 'https://platform.twitter.com/widgets.js');
      tweetScript.setAttribute('async', 'true');
      document.head.appendChild(tweetScript);
    }, 100);
  },
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
  background-color: #6ba7ff;
  border: dashed 2px #ffffff;
  border-left: 5px solid #ffa9ff;
  border-radius: 10px;
  box-shadow: 0 2px 6px rgba(0, 0, 0, 0.3);
}

#githubImg {
  height: 50px;
  width: 50px;
}
</style>
