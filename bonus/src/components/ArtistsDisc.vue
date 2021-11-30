<template>
    <div class="card-disc">
        <div>
            <img :src="discInfo.poster" :alt="discInfo.title + ' album'">
            <h3> {{discInfo.title}}</h3>
        </div>
        <div class="disc-info">
            <span>{{discInfo.author}}</span>
            <span>{{discInfo.year}}</span>
        </div>
    </div>
</template>

<script>
export default {
  name: 'ArtistsDisc',
  props: {
        discInfo: Object,
    },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
    .card-disc {
        display: flex;
        flex-flow: column nowrap;
        justify-content: space-between;
        background-color: var(--clr-primary-500);
        font-size: 1.2rem;
        padding: 1em;
        min-height: 30ch;
        text-align: center;
        position: relative;
        &:hover {
            bottom: .5rem;
            cursor: pointer;
        }
        &:hover img{
            filter: brightness(.8);
        }
        & img {
            width: 100%;
            aspect-ratio: 1;
            min-width: 120px;
        }
        & h3 {
            margin-top: 1rem;
        }
    }
    .disc-info {
        font-size: .9rem;
        margin-top: 1.5em;
        & span {
            display: block;
        }
    }
</style>