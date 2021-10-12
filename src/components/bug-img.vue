<template>
  <svg width="100%" height="100%" viewBox="0 0 100 100"
       xmlns="http://www.w3.org/2000/svg"
       xmlns:xlink="http://www.w3.org/1999/xlink">
    <filter id="displacementFilter">
      <feTurbulence type="turbulence" baseFrequency="0.3"
                    numOctaves="2" result="turbulence"/>
      <feDisplacementMap in2="turbulence" in="SourceGraphic"
                         scale="50" xChannelSelector="G" yChannelSelector="B"/>
    </filter>
    <image filter="url(#displacementFilter)" :href="testImg" x="0" y="0" height="100" width="100" />
  </svg>
</template>

<script>
import testImg from '../assets/1.png';

export default {
  name: "bug_img",
  data() {
    return {
      testImg,
    }
  }
}
</script>

<style scoped>

</style>
