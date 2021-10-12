<template>
  <svg viewBox="0 0 220 200" xmlns="http://www.w3.org/2000/svg" fill="black">
    <rect y="30" width="100" height="100">
      <animate attributeType="XML" attributeName="y" from="30" to="100"
               dur="5s" repeatCount="1" restart="always" />
    </rect>
    <rect x="120" y="30" width="100" height="100">
      <animate attributeType="XML" attributeName="y" from="30" to="100"
               dur="5s" repeatCount="1" restart="whenNotActive"/>
    </rect>
    <a id="restart"><text y="20">Restart animation</text></a>
  </svg>
</template>

<script>
export default {
  name: "TestSvg",
  mounted() {
    document.getElementById("restart").addEventListener("click", () => {
      document.querySelectorAll("animate").forEach(element => {
        element.beginElement();
      });
    });
  }
}
</script>

<style scoped>

</style>
