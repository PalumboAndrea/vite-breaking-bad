<script>
export default {
    data (){
        return {
            categoriesList: ['Alien', 'Laval', 'Vylon', 'Inzektor', 'Umi', 'Gusto'],
            selected: "",
        }
    }
}

</script>

<template>
    <div class="container">
        <div class="row">
            <div id="select-container" class="col-3 mb-3 p-3">
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
    }
</style>