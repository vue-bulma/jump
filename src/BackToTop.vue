<template>
  <div class="jump back-to-top" @click="scrollToTop" v-show="visible">
    <slot></slot>
  </div>
</template>

<script>
import jump from 'jump.js'
import { getScroll } from './util'

export default {
  props: {
    visibilityHeight: {
      type: Number,
      default: 400
    },
    options: {
      type: Object,
      default: () => ({})
    }
  },

  data () {
    return {
      visible: false
    }
  },

  mounted () {
    this.handleScroll()
    window.addEventListener('scroll', this.handleScroll)
  },

  beforeDestroy () {
    window.removeEventListener('scroll', this.handleScroll)
  },

  methods: {
    handleScroll () {
      this.visible = getScroll(window, true) > this.visibilityHeight
    },

    scrollToTop () {
      jump(document.body, this.options)
    }
  }
}
</script>

<style lang="scss">
.back-to-top {
  z-index: 10;
  position: fixed;
  right: 100px;
  bottom: 50px;
  cursor: pointer;
}
</style>
