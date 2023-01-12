<script>
import { store } from '../../store';
import AppLoader from '../components/AppLoader.vue';
import SelectCategory from '../components/SelectCategory.vue';
import axios from 'axios';

export default {
    name: 'AppMain',
    components: {
        AppLoader,
        SelectCategory,
  },
    data() {
        return {
            store,
            isLoading : true,
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
        setTimeout(this.changeLoading, 100)
    }
}
</script>

<template>
    <div id="main-wrapper" class="container-fluid py-5">
       
        <AppLoader v-if="isLoading" />
        <div v-else>
            <SelectCategory 
            @selectedCharacter="searchedCharacter"/>
            <div id="results-number-container" class="container p-5">
                <div class="row">
                    <div id="results-number" class="col-12 d-flex align-items-center">
                        <p class="m-0">
                            Found {{ store.cardsList.length }} cards
                        </p>
                    </div>
                </div>
                
                <section id="cards-container" class="my-3">
                    <div class="row d-flex justify-content-around">
                        <div v-for="card in store.cardsList" class="col-12 col-sm-6 col-md-4 col-lg-3 col-xxl-2 my-card text-center p-2 m-1">
                            <img :src="card.card_images[0].image_url" alt="" class="img-fluid">
                            <p class="name my-2">
                                {{card.name}}
                            </p>
                            <p class="type mb-2">
                                {{card.archetype}}
                            </p>
                        </div>
                    </div>
                </section> 
            </div>       
        </div>
        
    </div>
</template>

<style lang="scss" scoped>
    #main-wrapper{
        background-color: rgb(212,143,56);

        #results-number-container{
            background-color: white;
            border-radius: 10px;

            #results-number{
                height: 75px;
                background-color: rgb(32,37,41);
                border-radius: 10px;

                p:first-child{
                color: white;
            }
            }

            .my-card{
                background-color: rgb(212,143,56);
                border-radius: 10px;

                .name{
                    color: white;
                    font-weight: bold;
                    height: 50px;
                }

                .type{
                    color: black;
                }
            }
        }
    }
</style>

``