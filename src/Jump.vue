<template>
  <div class="jump">
    <slot></slot>
  </div>
</template>

<script>
import jump from 'jump.js'

export default {
  props: {
    target: String,
    options: {
      type: Object,
      default: () => ({})
    }
  },

  created () {
    this.$el = this.$el.nextSibling
  },

  mounted () {
    this.$el.addEventListener('click', this.handler)
  },

  methods: {
    handler () {
      jump(this.target, this.options)
    }
  }
}
</script>
