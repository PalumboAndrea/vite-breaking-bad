<script>
import {store} from '../../store';
import axios from 'axios';

export default {
    name: 'AppHeader',
    data(){
      return{
        store,
      }
    },
    methods:{
        getCharacters(){
            axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0', {
            })
            .then((response) => {
                this.store.cardsList = response.data.data;
            })
        }
    },
    created(){
        this.getCharacters();
    }
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
  #header-wrapper{
    height: 100px;

    img{
      height: 40px;
    }
  }

</style>
