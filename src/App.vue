<script>
import AppMain from './components/AppMain.vue'
import AppHeader from './components/AppHeader.vue'
import AppFooter from './components/AppFooter.vue';

export default{
  components: {
    AppHeader,
    AppMain,
    AppFooter,
},
  data(){
      return{
        
      }
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

  <footer>
    <AppFooter />
  </footer>
  
</template>

<style lang="scss">
@use './styles/partials/variable' as *;
@use './bootstrap/scss/bootstrap.scss' as *;
@use './styles/general.scss' as *;
@use './ldloader/index.css' as *;
</style>
