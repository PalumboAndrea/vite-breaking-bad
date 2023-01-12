<script>
import { store } from '../../store';

export default {
    data() {
        return {
            store,
        }
    },
}
</script>

<template>
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
</template>

<style lang="scss" scoped>
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
</style>