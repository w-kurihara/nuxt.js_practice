<template>
  <header class="compo-header">
    <p v-if="title">
      {{ title }}
    </p>
  </header>
</template>

<script>
export default {
  data () {
    return {
      title: null
    }
  },
  created () {
    const self = this
    this.$nuxt.$on('setHeader', ({
      title = null
    }) => {
      self.title = title
    })
  },
  beforeDestroy () {
    this.$nuxt.$off('setHeader')
  }
}
</script>

<style lang="sass" scoped>

.compo-header
  color: white
  height: 60px
  position: fixed
  left: 0
  right: 0
  top: 0
  margin: auto
  padding: 10px
  z-index: 1000

p
  color: white
  letter-spacing: .25em
  font-weight: bold
  text-align: center
  text-shadow: 0px 0px 5px #fff
</style>
