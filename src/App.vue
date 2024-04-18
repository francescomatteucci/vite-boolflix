<script>
  import AppContent from './components/AppContent.vue'
  import AppHeader from './components/AppHeader.vue'
  export default{
    components: {
      AppContent,
      AppHeader,
    }
  }

</script>

<template>
  <AppHeader />
  <AppContent />

</template>

<style lang="scss">
@use './style/general'
</style>