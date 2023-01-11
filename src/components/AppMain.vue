<script>
export default {
    name: 'AppMain',
    data() {
        return {

        }
    }
}
</script>

<template>
    <div id="main-wrapper" class="container-fluid pt-5">
        <div class="container p-5">
            <section id="cards-container" class="d-flex align-items-center">
                <p class="m-0 ms-3">
                    Found 39 cards
                </p>
            </section>

        </div>        
    </div>
</template>

<style lang="scss" scoped>
    #main-wrapper{
        height: 1000px;
        background-color: rgb(212,143,56);

        div{
            background-color: white;
            height: 1000px;

            #cards-container{
                background-color: rgb(32,37,41);
                height: 70px;

                p{
                    color: white;
                }
            }
        }
        
    }
</style>