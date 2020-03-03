<template>
  <transition name="fade">
      <a href="#" class="backtop trigger-backtop" role="button">
        <span>Back to top</span>
        <icon-base width="20" height="20" viewBox="0 0 96 66" icon-name="Arrow"><icon-Arrow /></icon-base>
      </a>
  </transition>
</template>
<script>
import iconBase from '@/components/icons/iconBase'
import iconArrow from '@/components/icons/iconArrow'
export default {
  name: "BackTop",
  components: {
    iconBase,
    iconArrow
  }
}
</script>
<style lang="scss" scoped>
.fade-enter-active, .fade-leave-active {
  transition: opacity .5s;
}
.fade-enter, .fade-leave-to {
  opacity: 0;
}
// back to top button
.backtop {
    position: fixed;
    bottom:-1px;
    right:20px;
    .dark-mode &{
      color:$white;
    }
    padding:1em 1.7em;
    @include align-center;
    span {
      font-size: $font-size-small;
        @include link-styled;
        display:inline-block;
        padding: 1em;
        @include transition;
    }
}
</style>