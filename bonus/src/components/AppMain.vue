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
        // return selectedGenre to parent(App)
        selectedGenre: String,
    },
    data() {
        return {
            genresArr: [],
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
                //get genres list
                this.discsArr.filter((item) => {
                    if(!this.genresArr.includes(item.genre)){
                        this.genresArr.push(item.genre);
                    }
                })
            })
            // used to send genreArray info to parent(App)
            this.$emit('genreOptions', this.genresArr)
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
        background-color: var(--clr-primary-800);
        padding: 50px 0;
        height: calc(100vh - 120px);
        overflow: auto;
    }
    #discs {
        width: 70%;
        margin: 0 auto;
        display: grid;
        grid-template-columns: repeat(5, 1fr);
        gap: 1rem
    }
</style>