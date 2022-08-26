<template>
   <div class="col">
    <div class="card text-center">
        <img :src="album.poster" class="card-img-top"/>
        <div class="card-body">
            <h3 class="card-title ms_separator">{{album.title}}</h3>
            <p class="card-text mt-4">{{album.author}}</p>
            <p class="card-text fw-bold">{{album.genre}}</p>
            <p class="card-text fw-bold">{{album.year}}</p>
        </div>
    </div>
  </div>
</template>

<script>
export default {
    name: 'SingleAlbum',
    props: {
        album: Object
    }
}
</script>

<style lang="scss">
    .ms_separator {
        position: relative;
        &::after {
            content: "";
            display: block;
            border-bottom: solid 1px #000;
            width: 20%;
            left: 40%;
            margin-top: 10px;
            position: absolute;
        }
    }
</style>