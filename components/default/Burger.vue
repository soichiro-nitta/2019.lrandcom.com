<template>
  <div
    class="Burger"
    @click="click"
  >
    <div
      ref="border1"
      class="border1"
    />
    <div
      ref="border2"
      class="border2"
    />
    <div
      ref="border3"
      class="border3"
    />
  </div>
</template>

<script>
import { TweenMax, Expo } from 'gsap'

export default {
  props: {
    opening: {
      type: Boolean,
      required: true
    },
    menu: {
      type: Boolean,
      required: true
    }
  },
  watch: {
    async opening() {
      await this.$delay(1000)
      this.in()
    },
    async menu(menu) {
      if (menu) {
        this.out()
      } else {
        await this.$delay(500)
        this.in()
      }
    }
  },
  mounted() {
    if (!this.opening) return
    this.in()
  },
  methods: {
    click() {
      this.$emit('openMenu')
    },
    in() {
      requestAnimationFrame(() => {
        TweenMax.to(this.$refs.border1, 0.7, {
          scaleX: 1,
          ease: Expo.easeOut
        })
        TweenMax.to(this.$refs.border2, 0.7, {
          scaleX: 1,
          ease: Expo.easeOut,
          delay: 0.1
        })
        TweenMax.to(this.$refs.border3, 0.7, {
          scaleX: 1,
          ease: Expo.easeOut,
          delay: 0.2
        })
      })
    },
    out() {
      requestAnimationFrame(() => {
        TweenMax.to(this.$refs.border1, 0.7, {
          scaleX: 0,
          ease: Expo.easeOut
        })
        TweenMax.to(this.$refs.border2, 0.7, {
          scaleX: 0,
          ease: Expo.easeOut,
          delay: 0.1
        })
        TweenMax.to(this.$refs.border3, 0.7, {
          scaleX: 0,
          ease: Expo.easeOut,
          delay: 0.2
        })
      })
    }
  }
}
</script>

<style lang="scss" scoped>
.Burger {
  position: fixed;
  top: 20px;
  right: 20px;
  width: 30px;
  height: 30px;
  // mix-blend-mode: difference;
  border-radius: 50%;
  .border1,
  .border2,
  .border3 {
    position: absolute;
    right: 0;
    left: 0;
    margin: auto;
    height: 2px;
    background: #fff;
    border-radius: 1px;
  }
  .border1 {
    top: 6px;
    width: 10px;
    transform: scaleX(0);
    transform-origin: center right;
  }
  .border2 {
    top: 14px;
    width: 15px;
    transform: scaleX(0);
    transform-origin: center left;
  }
  .border3 {
    top: 22px;
    width: 10px;
    transform: scaleX(0);
    transform-origin: center right;
  }
}
</style>
