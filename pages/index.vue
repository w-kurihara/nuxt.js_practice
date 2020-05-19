<template>
  <main class="page-index">
    <div>
      <p>a</p>
    </div>
  </main>
</template>

<script>
import { disableBodyScroll, clearAllBodyScrollLocks } from 'body-scroll-lock'

export default {
  components: {
  },
  mounted () {
    const page = document.querySelector('.page-index')
    disableBodyScroll(page)

    this.$nuxt.$emit('setHeader', {
      title: 'title'
    })
  },
  beforeDestory () {
    clearAllBodyScrollLocks()
  }
}
</script>

<style lang="sass" scoped>
.page-index
</style>
