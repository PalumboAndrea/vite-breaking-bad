<script>
export default {
    data (){
        return {
            categoriesList: ['Alien', 'Laval', 'Vylon', 'Inzektor', 'Umi', 'Gusto'],
            selected: null,
        }
    }
}

</script>

<template>
    <div class="container-fluid d-flex justify-content-center">
        <div class="row">
            <div id="select-container" class="pb-3" :class="(selected != null) ? 'mb-3' : ''">
                <div v-if="selected == null" class="my-3">
                    Seleziona una categoria:
                </div>
                <div v-else class="my-3">
                    Hai selezionato la categoria: {{ selected }}
                </div>
                <select name="" id="" class="form-select" v-model="selected" @change="$emit('selectedCharacter', selected)">
                    <option disabled value="">Seleziona una categoria</option>
                    <option v-for="archetypes in categoriesList"> {{ archetypes }} </option>
                </select>
            </div>
        </div>
    </div>
</template>

<style lang="scss" scoped>
    #select-container{
        background-color: white;
        border-radius: 10px;
        width: 400px;
    }
</style>