<template>
  <svg viewBox="0 0 100 100" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" id="container">
    <defs>
      <clipPath id="clipPath">
        <path
          ref="path"
          d="M 4 50 A 46 46 0 1 0 50 4 L 50 4 A 46 46 0 1 1 4 50 L 4 50 A 46 46 0 0 1 50 4 L 50 4 A 45 45 0 0 0 4 50">
          <animate
            attributeName="d"
            dur="0.3s"
            from=" M 4 50 A 46 46 0 1 0 50 4 L 50 4 A 46 46 0 1 1 4 50 L 4 50 A 46 46 0 0 1 50 4 L 50 4 A 45 45 0 0 0 4 50"
            to="M 4 50 A 46 46 0 1 0 50 4 L 50 49.9 A 0.1 0.1 0 1 1 49.9 50 L 4 50 A 46 46 0 0 1 50 4 L 50 49.9 A 0.1 0.1 0 0 0 49.9 50"
            fill="freeze"
            begin="indefinite"
            ref="lastAnimation"
          ></animate>
          <animate
            attributeName="d"
            dur="0.3s"
            from="M 4 50 A 46 46 0 1 0 50 4 L 50 49.9 A 0.1 0.1 0 1 1 49.9 50 L 4 50 A 46 46 0 0 1 50 4 L 50 49.9 A 0.1 0.1 0 0 0 49.9 50"
            to=" M 4 50 A 46 46 0 1 0 50 4 L 50 4 A 46 46 0 1 1 4 50 L 4 50 A 46 46 0 0 1 50 4 L 50 4 A 45 45 0 0 0 4 50"
            fill="freeze"
            begin="indefinite"
            ref="resetAnimation"
          ></animate>
        </path>
      </clipPath>
    </defs>
    <g ref="group">
      <circle cx="50"
              cy="50"
              r="47"
              stroke-width="0"
              fill="#45B26B"
              clip-path="url(#clipPath)"
      />
      <circle cx="50"
              cy="50"
              r="46"
              stroke-width="8"
              stroke="#CACACB"
              fill="rgba(255, 0, 0, 0)"
              stroke-linecap="round"
              stroke-dasharray="180, 160"
              id="bigPath"
      />
      <circle cx="50"
              cy="50"
              r="46"
              stroke-width="8"
              stroke="#3772FF"
              fill="none"
              stroke-linecap="round"
              stroke-dasharray="74, 250"
              ref="shortCircle"
      />

    </g>
    <path
      d="M 22 48 L 40 70 L 80 30"
      fill="none"
      stroke-width="6"
      stroke="#ffffff"
      stroke-dasharray="1,200"
      opacity="0"
      stroke-linejoin="round"
      stroke-linecap="round"
      ref="ok"
    >
    </path>
  </svg>
</template>

<script>

import gsap from 'gsap';

export default {
  name: "Loading",
  data() {
    return {
      startAnimation: null,
      completeTl: null,
    }
  },
  methods: {
    start() {
      if (this.startAnimation) {
        this.startAnimation.restart();
      } else {
        this.startAnimation = gsap.to(this.$refs.group, {
          duration: 1,
          repeat: -1,
          rotation: 360,
          transformOrigin: 'center',
          ease: 'none'
        });
      }
    },
    complete() {
      this.startAnimation.pause();
      const that = this;
      if (this.completeTl) {
        this.completeTl.restart();
      } else {
        this.completeTl = gsap.timeline();
        this.completeTl.to(this.$refs.shortCircle, {
          'stroke-dasharray': '300, 0',
          'stroke': '#45B26B',
          onComplete() {
            that.$refs.lastAnimation.beginElement();
          }
        });
        this.completeTl.to(this.$refs.ok, {
          'stroke-dasharray': '200,0',
          'opacity': '1',
          duration: 0.5,
        })
      }

    },
    reset() {
      this.$refs.resetAnimation.beginElement();
      this.completeTl.reverse();
      this.startAnimation.reverse();
    },
  },
}
</script>

<style scoped lang="scss">
#container {
  background: gray;
}
.circle-path {
  stroke-linecap: round;
}

#bigPath {
  transform: rotateZ(114deg);
  transform-origin: center;
}

#maskCircle {
  transform-origin: center;
}


</style>
