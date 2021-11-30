<template>
    <div class="card-disc">
        <div>
            <img :src="discInfo.poster" :alt="discInfo.title">
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
        background-color: #303A45;
        padding: 1.5em;
        min-height: 38ch;
        text-align: center;
        & img {
            width: 100%;
            aspect-ratio: 1;
            min-width: 120px;
        }
        & h3 {
            color: #fff;
            margin-top: 1rem;
        }
    }
    .disc-info {
        & span {
            display: block;
            color: #79756F;
        }
    }
</style>