<script>
import { store } from '../../store';
import AppLoader from '../components/AppLoader.vue';
import SelectCategory from '../components/SelectCategory.vue';
import CardsList from './CardsList.vue'
import axios from 'axios';

export default {
    name: 'AppMain',
    components: {
        AppLoader,
        SelectCategory,
        CardsList,
  },
    data() {
        return {
            store,
            isLoading : false,
        }
    },
    methods: {
        changeLoading (){
            this.isLoading = false;
        },
        searchedCharacter(selectedCategory){
            axios.get(`https://db.ygoprodeck.com/api/v7/cardinfo.php?archetype=${selectedCategory}`, {
              params: {
                category: selectedCategory,
              }
            })
            .then((response) => {
                this.store.cardsList = response.data.data; 
            })
        }
    },
    created(){
        setTimeout(this.changeLoading, 2000)
    }
}
</script>

<template>
    <div id="main-wrapper" class="container-fluid pt-3 pb-5">
       
        <div class="wrapper m-0">
            <SelectCategory 
            @selectedCharacter="searchedCharacter"/>
            <div id="results-number-container" class="container px-5 pt-4 pb-2" v-if="store.cardsList.length > 0">
                <div class="row">
                    <div id="results-number" class="col-12 d-flex align-items-center">
                        <p class="m-0">
                            Found {{ store.cardsList.length }} cards:
                        </p>
                    </div>
                </div>
                <CardsList />
            </div>       
        </div>
        
    </div>
</template>

<style lang="scss" scoped>
@use '../styles/partials/variable.scss' as *;

    #main-wrapper{
        background-color: rgb(212,143,56);
        height: $main-height;

        .wrapper{
            height: 100%;

            #results-number-container{
            background-color: white;
            border-radius: 10px;
            height: 85%;

                #results-number{
                    height: 75px;
                    background-color: rgb(32,37,41);
                    border-radius: 10px;

                    p:first-child{
                    color: white;
                    }
                }
            }
        }  
    }
</style>

``