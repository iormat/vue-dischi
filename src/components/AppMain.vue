<template>
    <main>
        <DiscsFilter @getResults="filteredDiscsArr"/>
        <section id="discs">
            <ArtistsDisc
            v-for="disc,i in showFiltered" :key="i"
            :discInfo="disc"
            />
        </section>
    </main>
</template>

<script>
import DiscsFilter from "./DiscsFilter.vue";
import ArtistsDisc from "./ArtistsDisc.vue";
import axios from "axios";

export default {
    name: 'AppMain',
    components: {
        ArtistsDisc,
        DiscsFilter,
    },
    data() {
        return {
            chosenGenre : "All",
            discsArr : [],
            apiUrl : 'https://flynn.boolean.careers/exercises/api/array/music',
        }
    },
    // hooks
    created () {
        // // get API
        this.getApiInfo()
    },
    // methods
    methods: {
        // get API's content funtion
        getApiInfo: function (){
            axios
                .get(this.apiUrl)
                .then((apiObj) =>  {
                this.discsArr = apiObj.data.response;
            })
        },
        // save child variable in parent data
        filteredDiscsArr(gotSelected) {
            this.chosenGenre = gotSelected;
        }
    },
    computed: {
        // check array to get only related results
        showFiltered() {
            if(this.chosenGenre === "All") {
                return this.discsArr;
            }
            return this.discsArr.filter((item) => {
                if(item.genre.toLowerCase() === this.chosenGenre.toLowerCase()){
                    return this.discsArr
                }
            })
        }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
    main {
        background-color: #212D3A;
        padding: 50px 0;
        height: 100vh;
        overflow: auto;
    }
    #discs {
        width: 70%;
        margin: 0 auto;
        display: grid;
        grid-template-columns: repeat(5, 1fr);
        gap: 1.5rem
    }
</style>