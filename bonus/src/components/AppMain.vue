<template>
    <main>
        <section id="discs">
            <ArtistsDisc
            v-for="disc,i in showFiltered" :key="i"
            :discInfo="disc"
            />
        </section>
    </main>
</template>

<script>
import ArtistsDisc from "./ArtistsDisc.vue";
import axios from "axios";

export default {
    name: 'AppMain',
    components: {
        ArtistsDisc,
    },
    props: {
        selectedGenre: String,
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
    },
    computed: {
        // check array to get only related results
        showFiltered() {
            if(this.selectedGenre === "All") {
                return this.discsArr;
            }
            return this.discsArr.filter((item) => {
                if(item.genre === this.selectedGenre){
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