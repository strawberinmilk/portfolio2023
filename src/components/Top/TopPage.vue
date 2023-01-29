<template>
  <div :id="$style.parent">
    <div :id="$style.inner">
      <h3>rin;</h3>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'TopPage',
});
</script>

<style lang="scss" module>
@use '@/constants/constants.scss';
#parent {
  position: relative;
  height: 700px;
}

#inner {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translateY(-50%) translateX(-50%);
  width: 70%;
  background-color: #62f6c5;
}
</style>
