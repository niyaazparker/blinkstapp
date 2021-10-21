

<template>
  <div id="app">
    <Security/>
  </div>
</template>

<script>
import Security from './components/Security.vue'

export default {
  name: 'App',
  components: {
    Security
  }
}
</script>
<style lang="scss">
@import "assets/sass/_shared.scss";
@import "assets/sass/_custom.scss";
</style>

