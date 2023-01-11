<script>
import AppMain from './components/AppMain.vue'
import AppHeader from './components/AppHeader.vue'

export default{
  components: {
    AppHeader,
    AppMain,
  }
}
</script>

<template>

  <header>
    <AppHeader />
  </header>


  <main>
    <AppMain />
  </main>
  
</template>

<style lang="scss">
@use './styles/general.scss' as *;
@use './styles/partials/variable' as *;
@use './bootstrap/scss/bootstrap.scss' as *;

</style>
