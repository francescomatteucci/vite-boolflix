<script>
import AppContent from './components/AppContent.vue'
import AppHeader from './components/AppHeader.vue'
export default {
  components: {
    AppContent,
    AppHeader,
  }
}

</script>

<template>
  <div id="app">
    <AppHeader />
    <AppContent />
  </div>

</template>

<style lang="scss">
@use './style/general';
</style>