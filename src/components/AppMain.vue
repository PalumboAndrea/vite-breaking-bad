<script>
import { store } from '../../store';
import axios from 'axios';

export default {
    name: 'AppMain',
    data() {
        return {
            store,
            cardsList : [],
        }
    },
    methods:{
        getCharacters(){
            axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0', {
            })
            .then((response) => { 
                console.log(response.data.data[0].archetype)
                this.cardsList = response.data.data;
            })
        }
    },
    created(){
        this.getCharacters();
    }
}
</script>

<template>
    <div id="main-wrapper" class="container-fluid py-5">
        <div class="container p-5">
            <p class="m-0 ps-3 d-flex align-items-center">
                Found 39 cards
            </p>
            <section id="cards-container" class="d-flex flex-wrap justify-content-between mb-2">
                <div v-for="card in cardsList" class="my-card text-center">
                    <img :src="card.card_images[0].image_url" alt="">
                    <p class="name mt-1">
                        {{card.name}}
                    </p>
                    <p class="type">
                        {{card.archetype}}
                    </p>
                    
                </div>
            </section>

        </div>        
    </div>
</template>

<style lang="scss" scoped>
    #main-wrapper{
        background-color: rgb(212,143,56);

        div:first-child{
            background-color: white;
            border-radius: 10px;

            p:first-child{
                color: white;
                background-color: rgb(32,37,41);
                height: 70px;
            }

            .my-card{
                height: 430px;
                width: calc(100% / 5 - 15px);
                margin: 15px 0;
                background-color: rgb(212,143,56);
                position: relative;
                border-radius: 10px;

                img{
                    width: 100%;
                }

                .name{
                    color: white;
                    font-weight: bold;
                }

                .type{
                    color: black;
                    position: absolute;
                    left: 50%;
                    bottom: 10px;
                    transform: translate(-50%);
                }
                
            }
            
        }
        
    }
</style>