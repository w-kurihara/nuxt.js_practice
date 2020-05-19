<template>
  <div class="root-wrapper">
    <p v-for="i in 10" :key="i" class="firefly" />
    <Header />
    <nuxt class="main" />
  </div>
</template>

<script>
import Header from '~/components/Header'

export default {
  components: {
    Header
  }
}
</script>

<style lang="sass" scoped>
$quantity: 10

.root-wrapper
  margin: 0 auto
  width: 100%
  min-height: 100vh
  background: url('/nuxt.js_practice/bg.jpg')
  background-size: cover
  background-color: rgba(0,0,0,0.5)
  background-blend-mode: darken
  .firefly
    position: fixed
    left: 50%
    top: 50%
    width: 3px
    height: 3px
    animation: ease 200s alternate infinite
    pointer-events: none
    &::before,
    &::after
      content: ''
      position: absolute
      width: 100%
      height: 100%
      border-radius: 50%
      transform-origin: -10vw
    &::before
      background: red
      opacity: 0.4
      animation: drift ease alternate infinite
    &::after
      background: white
      opacity: 1
      box-shadow: 0 0 0vw 0vw red
      animation: drift ease alternate infinite, flash ease infinite
// Randomize Fireflies Motion
// Source: https://codepen.io/mikegolus/pen/Jegvym

@for $i from 1 through $quantity
  $steps: random(10) + 10
  $rotationSpeed: random(25) + 15s
  .firefly:nth-child(#{$i})
    animation-name: move#{$i}
    &::before
      animation-duration: #{$rotationSpeed}
    &::after
      animation-duration: #{$rotationSpeed}, random(6000) + 5000ms
      animation-delay: 0ms, random(8000) + 500ms
  @keyframes move#{$i}
    @for $step from 0 through $steps
      #{$step * (100 / $steps)}%
        transform: translateX(random(100) - 50vw) translateY(random(100) - 50vh) scale(random(100) / 100)

@keyframes drift
  0%
    transform: rotate(0deg)
  100%
    transform: rotate(360deg)

@keyframes flash
  0%,100%
    opacity: .5
    box-shadow: 0 0 5px 5px green
  50%
    opacity: 1
    box-shadow: 0 0 10px 5px green
</style>
