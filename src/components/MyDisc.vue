<template>
   <div class="disc p-3 text-center">
        <div class="p-3">
            <img :src="disc.poster" :alt="disc.name" class="img-fluid mb-3"/>
            <p class="title text-uppercase fw-bold">{{disc.title}}</p>
            <p class="author lead mb-0">{{disc.author}}</p>
            <p class="year">{{disc.year}}</p>
        </div>
  </div>
</template>

<script>
export default {
    name: 'MyDisc',
    props: {
        disc: Object,
    }
}
</script>

<style lang="scss" scoped>
    @import '@/styles/vars.scss';
    .disc {
        flex-basis: calc(100% / 5);

        div {
            background-color: $color_card;
            height: 100%;
        }

        .title {
            color:$color_text1;
        }

        .author, .year {
            color: $color_text2;
        }
    }
</style>