<template>
  <div :id="$style.parent">
    <div :id="$style.inner">
      <h3>TopQualification</h3>
      <h5>第二種電気工事士</h5>
      <p>一軒家とかコンビニくらいまでの建物の電気工事ができる。</p>
      <h5>認定電気工事従事者</h5>
      <p>高圧受電の建物(ビルとか)でも低圧の範囲なら電気工事ができる。</p>
      <p>二つ合わせるとどんな建物でもコンセントくらいは触れる。</p>
      <p>でもIT屋さんなので自宅のコンセントを抜け止めにしたり増やしたりくらいで実質ペーパー</p>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'TopQualification',
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
  background-color: #c5f9ff;
  border: dashed 2px #ffffff;
  border-left: 5px solid #ffa9ff;
  border-radius: 10px;
  box-shadow: 0 2px 6px rgba(0, 0, 0, 0.3);
}
</style>
