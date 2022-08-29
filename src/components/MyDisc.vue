<template>
   <div class="disc p-3 text-center">
        <div class="p-3">
            <img :src="element.poster" :alt="element.name" class="img-fluid mb-3"/>
            <p class="title text-uppercase fw-bold">{{element.title}}</p>
            <p class="author lead mb-0">{{element.author}}</p>
            <p class="year">{{element.year}}</p>
        </div>
  </div>
</template>

<script>
export default {
    name: 'MyDisc',
    props: {
        element: Object,
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