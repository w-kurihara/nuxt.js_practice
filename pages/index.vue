<template>
  <main class="page-index">
    <div>
      <p>a</p>
    </div>
  </main>
</template>

<script>

export default {
  components: {
  },
  mounted () {
    this.$nuxt.$emit('setHeader', {
      title: 'title'
    })
  }
}
</script>

<style lang="sass" scoped>
.page-index
</style>
