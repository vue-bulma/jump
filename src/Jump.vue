<template>
  <slot></slot>
</template>

<script>
import jump from 'jump.js'
import { on } from './util'

export default {
  props: {
    target: String,
    options: {
      type: Object,
      default: () => ({})
    }
  },

  compiled () {
    this.$el = this.$el.nextSibling
  },

  ready () {
    on(this.$el, 'click', this.handler)
  },

  methods: {
    handler () {
      jump(this.target, this.options)
    }
  }
}
</script>
