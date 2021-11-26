<template>
    <main>
        <section id="discs">
            <ArtistsDisc
            v-for="disc,i in discsArr" :key="i"
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
    data() {
        return {
            discsArr : [],
        }
    },
    created () {
        axios
            .get('https://flynn.boolean.careers/exercises/api/array/music')
            .then((apiObj) => {
            this.discsArr = apiObj.data.response;
        })            
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