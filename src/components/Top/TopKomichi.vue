<template>
  <div :id="$style.parent">
    <div :id="$style.inner">
      <h3>小路綾bot</h3>
      <el-row>
        <el-col :span="0" :sm="12">
          <a
            class="twitter-timeline"
            data-height="500"
            data-theme="light"
            href="https://twitter.com/komichiAyaBot?ref_src=twsrc%5Etfw"
            >Tweets by komichiAyaBot</a
          >
        </el-col>
        <el-col :span="24" :sm="12">
          <a
            href="https://twitter.com/komichiayabot?ref_src=twsrc%5Etfw"
            class="twitter-follow-button"
            data-show-count="false"
            >Follow @komichiayabot</a
          >
          <p>小路綾とは、"きんいろモザイク"という漫画、アニメの登場人物。</p>
          <p>その小路綾の発言を形態素解析し、マルコフ連鎖により小路綾らしい発言を生成する。</p>
          <p>
            twitterでは、10分に一度ランダムに生成したテキストを投稿する機能、リプライを受け取りそのテキストを形態素解析し、
            動詞等を抜き取りその単語から開始される文章を生成し擬似的に会話をすることができる機能が搭載されている。
          </p>
        </el-col>
      </el-row>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive } from 'vue';

export default defineComponent({
  name: 'TopKomichi',
  setup() {
    const state = reactive({
      width: window.innerWidth,
    });
    return {
      state,
    };
  },
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
  background-color: #a260bf;
  border: dashed 2px #ffffff;
  border-left: 5px solid #ffa9ff;
  border-radius: 10px;
  box-shadow: 0 2px 6px rgba(0, 0, 0, 0.3);
}
</style>
