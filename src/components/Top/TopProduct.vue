<template>
  <div :id="$style.parent">
    <div :id="$style.inner">
      <h3>Product</h3>

      <div>
        <p>2021年版ポートフォリオ<br />目に悪いってめっちゃ言われる</p>
        <a href="https://strawberinmilk.github.io/vue-portfolio/">2021年版ポートフォリオ</a>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'TopProduct',
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
  background-color: #c0c0e0;
}
</style>
