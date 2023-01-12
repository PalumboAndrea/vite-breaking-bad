<script>

export default {
    name: 'AppHeader',
}
</script>

<template>
  <div id="header-wrapper" class="container-fluid d-flex align-items-center px-4">
    <img src="../assets/img/Yu-Gi-Oh!_(Logo).jpg" alt="" class="me-3">
    <h1 class="m-0">
      Yu-Gi-Oh Api
    </h1>
  </div>
  
  
</template>

<style lang="scss" scoped>
@use '../styles/partials/variable.scss' as *;

  #header-wrapper{
    height: $header-height;

    img{
      height: 40px;
    }
  }

</style>
